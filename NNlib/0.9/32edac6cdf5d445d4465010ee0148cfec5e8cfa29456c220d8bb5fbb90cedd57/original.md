```
sigmoid_fast(x)
```

This is a faster, and very slightly less accurate, version of `sigmoid`. For `x::Float32`, perhaps 3 times faster, and maximum errors 2 eps instead of 1.

See also [`tanh_fast`](@ref).

```julia-repl
julia> sigmoid(0.2f0)
0.54983395f0

julia> sigmoid_fast(0.2f0)
0.54983395f0

julia> hardσ(0.2f0)
0.53333336f0
```
