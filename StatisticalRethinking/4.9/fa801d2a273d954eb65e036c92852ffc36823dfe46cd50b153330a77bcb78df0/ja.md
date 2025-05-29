# link

一般化リンク関数は、データフレーム内のすべてのパラメータに対して呼び出し可能なものをx値の範囲で評価します。

```julia
link(dfa, rx_to_val, xrange)

```

## 必要な引数

  * `dfa::DataFrame`: パラメータを含むデータフレーム
  * `rx_to_val::Function`: 2つの引数を持つ関数：行オブジェクトとx
  * `xrange`: 評価されるx値のシーケンス

## 戻り値

xrangeの各値に基づいて計算された各エントリを持つベクトルです。各エントリはデータフレームの各行に対応するリストです。

## 例

```jldoctest
julia> using StatisticalRethinking, DataFrames

julia> d = DataFrame(:a => [1,2], :b=>[1,1])
2×2 DataFrame
 Row │ a      b
     │ Int64  Int64
─────┼──────────────
   1 │     1      1
   2 │     2      1

julia> link(d, (r,x) -> r.a+x*r.b, 1:2)
2-element Vector{Vector{Int64}}:
 [2, 3]
 [3, 4]

```
