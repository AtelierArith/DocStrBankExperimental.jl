```
PinkNoise <: AbstractNoise
```

`SignalAnalysis.jl`の実装を使用してピンクノイズを生成するための型です。

ノイズ値は標準正規分布𝒩(μ=0, σ=1)からサンプリングされます。つまり、約95%の値は約-2から約2の間にあります（`noiselevel = 1`の場合）。 ヒント: 手動でノイズサンプルを作成するには、[`simulate_noise`](@ref)関数を使用してください。

# フィールド

  * `noiselevel = 1`（オプション）: ノイズをスケーリングするために使用される係数。
  * `func = SignalAnalysis.PinkGaussian`（オプション）: ノイズサンプルを作成するために使用される関数。このフィールドは内部使用のためのものであり、通常はユーザーによって直接変更されるべきではありません。このフィールドの変更は予期しない動作を引き起こす可能性があります。

# 例

```julia-repl
julia> noise = PinkNoise(noiselevel = 3)
PinkNoise
  noiselevel: Int64 3
  func: UnionAll

julia> using StableRNGs

julia> simulate_noise(StableRNG(1), noise, 5)
5-element Vector{Float64}:
 2.578878369756878
 3.4972108606501786
 2.878568584946028
 2.2725654770788384
 3.5291669151888683
```

[`RedNoise`](@ref)、[`WhiteNoise`](@ref)、[`ExponentialNoise`](@ref)、[`NoNoise`](@ref)も参照してください。
