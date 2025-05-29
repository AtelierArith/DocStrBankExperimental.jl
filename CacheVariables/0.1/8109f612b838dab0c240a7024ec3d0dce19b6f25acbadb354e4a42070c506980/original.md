```
cache(f, path; mod = @__MODULE__)
```

Cache output from running `f()` using BSON file at `path`. Load if the file exists; run and save if it does not. Use `mod` keyword argument to specify module.

Tip: Use `do...end` to cache output from a block of code.

# Examples

```julia-repl
julia> cache("test.bson") do
         a = "a very time-consuming quantity to compute"
         b = "a very long simulation to run"
         return (; a = a, b = b)
       end
[ Info: Saving to test.bson
(a = "a very time-consuming quantity to compute", b = "a very long simulation to run")

julia> cache("test.bson") do
         a = "a very time-consuming quantity to compute"
         b = "a very long simulation to run"
         return (; a = a, b = b)
       end
[ Info: Loading from test.bson
(a = "a very time-consuming quantity to compute", b = "a very long simulation to run")
```
