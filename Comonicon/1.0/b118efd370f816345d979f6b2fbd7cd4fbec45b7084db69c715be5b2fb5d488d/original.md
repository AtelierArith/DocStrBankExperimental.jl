```
cmd_error(msg::String, code::Int = 1)
```

Throw a `CommandError` with message `msg` and return code `code`. This is preferred as exception handle when writing a CLI compatible Julia program.

When the program is running in normal Julia execution the error will print as normal Julia exception with stacktrace.

When the progrm is running from a CLI entry, the exception is printed as standard CLI exceptions with exit code (default is `1`). Then the corresponding help message is printed.
