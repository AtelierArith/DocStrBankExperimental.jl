```
append!(xf::Transducer, dest, src) -> dest
```

This API is modeled after [`into` in Clojure](https://clojure.github.io/clojure/clojure.core-api.html#clojure.core/into).

!!! warning
    The performance of `append!(dest, src::Eduction)` is poor. Use `append!!` instead if two-argument form is preferred.


# Examples

```jldoctest
julia> using Transducers

julia> append!(Drop(2), [-1, -2], 1:5)
5-element Vector{Int64}:
 -1
 -2
  3
  4
  5
```
