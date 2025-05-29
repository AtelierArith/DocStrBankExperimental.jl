```
logitbinarycrossentropy(ŷ, y; agg = mean)
```

Mathematically equivalent to [`binarycrossentropy(σ(ŷ), y)`](@ref) but is more numerically stable.

See also: [`crossentropy`](@ref), [`logitcrossentropy`](@ref).

# Examples

```jldoctest
julia> y_bin = Bool[1,0,1];

julia> y_model = Float32[2, -1, pi]
3-element Vector{Float32}:
  2.0
 -1.0
  3.1415927

julia> Flux.logitbinarycrossentropy(y_model, y_bin)
0.160832f0

julia> Flux.binarycrossentropy(sigmoid.(y_model), y_bin)
0.16083185f0
```
