```
NoNoise <: AbstractNoise
```

ノイズなしのシミュレーション用の型; ノイズの代わりにゼロを返します。

ヒント: 手動でノイズサンプルを作成するには、[`simulate_noise`](@ref) 関数を使用してください。

# 例

```julia-repl
julia> noise = NoNoise()
NoNoise()

julia> using StableRNGs

julia> simulate_noise(StableRNG(1), noise, 3)
3-element Vector{Float64}:
 0.0
 0.0
 0.0
```

他にも [`PinkNoise`](@ref), [`RedNoise`](@ref), [`ExponentialNoise`](@ref), [`WhiteNoise`](@ref) を参照してください。
