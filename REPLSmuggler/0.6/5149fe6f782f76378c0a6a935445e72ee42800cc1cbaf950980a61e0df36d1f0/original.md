```
smuggle(exception, stackframes=stacktrace(Base.catch_stacktrace()))
```

Smuggle an exception. Can be used to report on exceptions thrown by code evaluated by the user in the REPL.

!!! warning
    The notification will be sent to all connected sessions.


# Examples

```julia
try
    error("foo")
catch exc
    smuggle(exc)
end
```
