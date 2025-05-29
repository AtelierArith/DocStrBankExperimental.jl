# PI

データのパーセンタイル中央区間を計算します。境界のベクトルを返します。

```julia
PI(data; perc_prob)

```

## 必要な引数

  * `data`: データ値を反復可能なもの

## オプションの引数

  * `perc_prob::Float64=0.89`: 計算するパーセンタイル区間

## 例

```jldoctest
julia> using StatisticalRethinking

julia> PI(1:10)
2-element Vector{Float64}:
 1.495
 9.505

julia> PI(1:10; perc_prob=0.1)
2-element Vector{Float64}:
 5.05
 5.95

```
