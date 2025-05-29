Differences to stdlib/Logging/ConsoleLogger:

```
- default timestamp on logging messages (except @info)
- a 'shouldlog' function can be passed in. The `shouldlog_default` function filters
    on HTTP.Servers messages as well as on message_limits
- :wslog => true flag which may be used for context-sensitive output
    from 'show' methods. This means a user can define 'show' methods
    which are used with this logger without affecting the behaviour
    defined in other modules.
- :limited => true is included in the default IOContext. Keyword: show_limited
- string_with_env_ws is exported for easy overloading on specific types
- @info, @debug, @warn etc. will splat the first argument if it's a tuple arguments, e.g.

julia> var = "a"
"a"
julia> @info (1, var)
[ Info: 1a
```
