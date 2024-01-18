# Go Logger interface – Logrus implementation

This library provides an implementation of the [Logger interface](https://github.com/secondtruth/go-logger)
for [Logrus](https://github.com/sirupsen/logrus).

## Installation

To install `go-logger-logrus`, use the following command:

	go get -u github.com/secondtruth/go-logger-logrus

## Quick Start

```go
package main

import (
	"os"

	logruslogger "github.com/secondtruth/go-logger-logrus/logger"
	"github.com/secondtruth/go-logger/logger"
	"github.com/sirupsen/logrus"
)

func main() {
	logrusLog := logrus.New()
	logrusLog.SetFormatter(&logrus.JSONFormatter{})
	logrusLog.SetOutput(os.Stdout)
	logrusLog.SetLevel(logrus.DebugLevel)
	log, _ := logruslogger.NewLogrusLogger(logrusLog)
	
	log.WithFields(logger.Fields{
		"foo": "bar",
	}).Info("message")
}
```
