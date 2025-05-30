# シミュレーション

呼び出し可能な分布からサンプリングする予測の一般的なシミュレーション。

```julia
simulate(df, rx_to_dist, xrange; return_dist, seed)

```

## 必須引数

  * `df::DataFrame`: 各行にパラメータを持つデータフレーム
  * `rx_to_dist::Function`: 行オブジェクトとx値の2つの引数を持つ呼び出し可能な関数。`Distribution`インスタンスを返す必要があります。
  * `xrange`: 引数を持つイテラブル

## オプション引数

  * `return_dist::Bool = false`: `true`に設定すると、サンプルではなく分布が返されます
  * `seed::Int = missing`: ランダムシードを設定します

## 戻り値

各アイテムがxrange引数のすべてのアイテムから生成されたベクター。各アイテムは再び、分布を取得するための`rx_to_dist`呼び出しから得られたベクターです。そしてそれからサンプリングされます。引数`return_dist=true`の場合、サンプリングステップは省略されます。

## 例

```jldoctest
julia> using StatisticalRethinking, DataFrames, Distributions

julia> d = DataFrame(:mu => [1.0, 2.0], :sigma => [0.1, 0.2])
2×2 DataFrame
 Row │ mu       sigma
     │ Float64  Float64
─────┼──────────────────
   1 │     1.0      0.0
   2 │     2.0      0.0

julia> simulate(d, (r,x) -> Normal(r.mu+x, r.sigma), 0:1)
2-element Vector{Vector{Float64}}:
 [1.0, 2.0]
 [2.0, 3.0]

julia> simulate(d, (r,x) -> Normal(r.mu+x, r.sigma), 0:1, return_dist=true)
2-element Vector{Vector{Normal{Float64}}}:
 [Normal{Float64}(μ=1.0, σ=0.0), Normal{Float64}(μ=2.0, σ=0.0)]
 [Normal{Float64}(μ=2.0, σ=0.0), Normal{Float64}(μ=3.0, σ=0.0)]

```
