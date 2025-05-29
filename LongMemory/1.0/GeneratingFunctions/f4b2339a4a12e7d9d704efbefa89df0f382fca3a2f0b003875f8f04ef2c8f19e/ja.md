```
fracdiff(x,d)
```

時系列 `x` の分数差分を、分数次数 `d∈(-1/2,1/2)` で計算します。

# 引数

  * `x::Vector`: 時系列
  * `d::Float64`: 分数差分パラメータ

# 出力

  * `dx::Vector`: `x` の分数差分

# 注意事項

この関数は、高速フーリエ変換を使用して、時系列と分数差分フィルターの畳み込みを計算します。詳細については、[Jensen and Nielsen (2014)](https://onlinelibrary.wiley.com/doi/10.1111/jtsa.12074)を参照してください。分数差分フィルターの係数を効率的に計算するために、自己回帰式を使用します。

# 例

```julia-repl
julia> fracdiff(randn(100,1),0.4)
```
