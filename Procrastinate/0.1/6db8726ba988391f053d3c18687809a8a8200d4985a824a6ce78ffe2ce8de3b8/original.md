```
Deferred
```

A struct representing a value that is computed only when needed and only once.

It is most useful for computing expensive members of `struct`s that may or may not ever be used.  By deferring the computation, the cost is avoided if the datum is  never used.

`Deferred` takes advantage of closures to ensure that the necessary data will be  available when needed.   `Deferred` is thread safe.

# Example:

```julia-repl
julia> using Procrastinate
julia> d = Deferred() do
    # Some expensive computation
    println("Computing!")
    return "result"
end
julia> d()
Computing!
"result"
julia> d()
"result"
```
