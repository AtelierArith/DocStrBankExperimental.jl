```
coeftable(fit::HDMModel, names::Vector{String}=string.(1:length(fit.fixef)))
```

モデルから*選択された*係数、すなわち0に設定されていない係数のテーブルを返します。

# 引数

  * `fit::HDMModel`: フィッティングされたモデル。
  * `names::Vector{String}`: モデル内のすべての係数の名前（選択されたものだけでなく）、デフォルトは整数名

# 戻り値

`StatsBase.CoefTable`オブジェクト。
