Redirects log events to multiple loggers. The primary use case is to allow logging to both a file and the console. Secondarily, it can track the counts of all log messages.

# Example

```Julia
MultiLogger([TerminalLogger(stderr), SimpleLogger(stream)], LogEventTracker())
```
