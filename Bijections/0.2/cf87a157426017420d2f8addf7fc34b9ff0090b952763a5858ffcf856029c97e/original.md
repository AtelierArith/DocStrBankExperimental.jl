```
Bijection()
```

Construct a new `Bijection`. 

  * `Bijection{S,T}()` creates an empty `Bijection` from objects of type `S` to objects of type `T`. If `S` and `T` are omitted, then we have `Bijection{Any,Any}`.
  * `Bijection(x::S, y::T)` creates a new `Bijection` initialized with `x` mapping to `y`.
  * `Bijection(dict::Dict{S,T})` creates a new `Bijection` based on the mapping in `dict`.
  * `Bijection(pair_list::Vector{Pair{S,T}})` creates a new `Bijection` using the key/value pairs in `pair_list`.
