```
logitbinarycrossentropy(ŷ, y; agg = mean)
```

数学的には [`binarycrossentropy(σ(ŷ), y)`](@ref) と同等ですが、数値的に安定しています。

関連情報: [`crossentropy`](@ref), [`logitcrossentropy`](@ref).

# 例

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
