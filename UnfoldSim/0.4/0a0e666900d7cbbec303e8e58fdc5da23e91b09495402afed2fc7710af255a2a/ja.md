```
ExponentialNoise <: AbstractNoise
```

ARスペクトルにおける指数減衰を持つノイズを生成するための型です。

ヒント: 手動でノイズサンプルを作成するには、[`simulate_noise`](@ref) 関数を使用してください。

!!! warning
    現在の実装では、全体の自己回帰（AR）スペクトルにわたって指数減衰を得ようとしています。これはNサンプル（信号内のサンプルの総数）にわたる長さです。これには、サイズNxNのコレスキー行列の逆行列が必要であり、非自明な問題には大量のRAMが必要です。


# フィールド

  * `noiselevel = 1`（オプション）: ノイズをスケールするために使用される係数。
  * `ν = 1.5`（オプション）: AR減衰の指数係数「nu」。

# 例

```julia-repl
julia> noise = ExponentialNoise()
ExponentialNoise
  noiselevel: Int64 1
  ν: Float64 1.5

julia> using StableRNGs

julia> simulate_noise(StableRNG(1), noise, 5)
5-element Vector{Float64}:
  -5.325200748641231
  -3.437402125380177
   2.7852625669058884
  -1.5381022393382109
 -14.818799857226612
```

他にも [`PinkNoise`](@ref)、[`RedNoise`](@ref)、[`NoNoise`](@ref)、[`WhiteNoise`](@ref) を参照してください。
