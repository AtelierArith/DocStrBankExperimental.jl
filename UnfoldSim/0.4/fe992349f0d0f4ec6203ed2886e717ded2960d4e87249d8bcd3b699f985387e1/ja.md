```
RedNoise <: AbstractNoise
```

`SignalAnalysis.jl` 実装を使用して赤色ノイズを生成するための型です。

ノイズ値は標準正規分布 𝒩(μ=0, σ=1) からサンプリングされます。つまり、約95%の値は約-2から約2の間にあります（`noiselevel = 1` の場合）。 ヒント: 手動でノイズサンプルを作成するには、[`simulate_noise`](@ref) 関数を使用してください。

# フィールド

  * `noiselevel = 1`（オプション）: ノイズをスケーリングするために使用される係数。
  * `func = SignalAnalysis.RedGaussian`（オプション）: ノイズサンプルを作成するために使用される関数。このフィールドは内部使用のためのものであり、通常はユーザーによって直接変更されるべきではありません。このフィールドの変更は予期しない動作を引き起こす可能性があります。

# 例

```julia-repl
julia> noise = RedNoise(noiselevel = 2)
RedNoise
  noiselevel: Int64 2
  func: UnionAll

julia> using StableRNGs

julia> simulate_noise(StableRNG(2), noise, 3)
3-element Vector{Float64}:
 -0.34153942884005967
 -0.4651387715669636
 -0.4951538876376382
```

他にも [`PinkNoise`](@ref), [`WhiteNoise`](@ref), [`ExponentialNoise`](@ref), [`NoNoise`](@ref) を参照してください。
