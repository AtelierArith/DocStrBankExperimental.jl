```
@withprogress [name=""] [parentid=uuid4()] ex
```

Create a lexical environment in which [`@logprogress`](@ref) can be used to emit progress log events without manually specifying the log level, `_id`, and name (log message).

```julia
@withprogress name="iterating" begin
    for i = 1:10
        sleep(0.5)
        @logprogress i/10
    end
end
```
