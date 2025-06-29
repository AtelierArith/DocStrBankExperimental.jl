```
try_with_timeout(f, timeout, T=Any) -> T
```

Run `f` in a new task, and return its result. If `f` does not complete within `timeout` seconds, throw a `TimeoutException`. If `f` throws an exception, rethrow it. If `f` completes successfully, return its result. `f` should be of the form `f(x::TimedOut)`, where `x` is a `TimedOut` object. This allows the calling function to check whether the timeout has been reached by checking `x[]` and if `true`, the timeout was reached and the function can cancel/abort gracefully. The 3rd argument `T` is optional (default `Any`) and allows passing an expected return type that `f` should return; this allows avoiding a dynamic dispatch from non-inferability of using `try_with_timeout` with `f`.

# Examples

```julia
julia> try_with_timeout(_ -> 1, 1)
1

julia> try_with_timeout(_ -> sleep(3), 1)
ERROR: TimeoutException: try_with_timeout timed out after 1.0 seconds
Stacktrace:
 [1] try_with_timeout(::var"#1#2", ::Int64) at ./REPL[1]:1
 [2] top-level scope at REPL[2]:1

julia> try_with_timeout(_ -> error("hey"), 1)
ERROR: hey
Stacktrace:
 [1] error(::String) at ./error.jl:33
 [2] (::var"#1#2")(::TimedOut{Any}) at ./REPL[1]:1
 [3] try_with_timeout(::var"#1#2", ::Int64) at ./REPL[1]:1
 [4] top-level scope at REPL[3]:1

julia> try_with_timeout(_ -> 1, 1, Int)
1

# usage with `TimedOut`
julia> try_with_timeout(1) do timedout
    while !timedout[]
        # do iterative computation that may take too long
    end
end

julia> try_with_timeout(1) do timedout
    sleep(3)
    timedout[] && abort_gracefully()
end
```
