```
DefaultFormatter
```

The `DefaultFormatter` uses a simple format string to build the log message. Fields from the `Record` to be used should be wrapped curly brackets.

Ex) "[{level} | {name}]: {msg}" will print message of the form [info | root]: my info message. [warn | root]: my warning message. ...
