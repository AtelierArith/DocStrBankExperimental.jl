```
(advice::Advice)((post::Function, func::Function, args::Tuple, kwargs::NamedTuple))
```

Apply `advice` to the function call `func(args...; kwargs...)`, and return the new `(post, func, args, kwargs)` tuple.
