# lppd

Log Pointwise Predictive Density計算の一般的なバージョンで、`simulate`関数に似ていますが、ターゲット値の対数密度も追加で計算します。

```julia
lppd(df, rx_to_dist, xseq, yseq)

```

## 必要な引数

  * `df::DataFrame`: パラメータを含むデータフレーム
  * `rx_to_dist::Function`: 行オブジェクトとx値の2つの引数を持つ呼び出し可能な関数。

`Distribution`インスタンスを返す必要があります。

  * `xseq`: 呼び出し可能な関数に渡されるx値のシーケンス
  * `yseq`: 対数密度計算のためのターゲット値のシーケンス。

## 戻り値

`xseq`と`yseq`と同じサイズの浮動小数点値のベクター。

## 例

```jldoctest
julia> using StatisticalRethinking, DataFrames, Distributions

julia> df = DataFrame(:mu => [0.0, 1.0])
2×1 DataFrame
 Row │ mu
     │ Float64
─────┼─────────
   1 │     0.0
   2 │     1.0

julia> lppd(df, (r, x) -> Normal(r.mu + x, 1.0), 0:3, 3:-1:0)
4-element Vector{Float64}:
 -3.5331959794720684
 -1.1380087295845114
 -1.9106724357818656
 -6.082335295491998
```
