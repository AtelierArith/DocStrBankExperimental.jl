```
var[std](rr::Union{AbstractVector{<:RegressionModel}, RegressionModel})
var[std](data::Union{IterateFixedTable, FixedTable}; minobs=0.8)
```

回帰モデルが渡されると、これは残差平方和を自由度で割ったものに基づいて分散（標準偏差）を計算します。RegressionModelのベクトルは、同じ長さのベクトル結果を返します。

FixedTable（またはIterateFixedTable）が渡され、かつそれが1列のみを含む場合、その列の分散（標準偏差）が計算されます。2列ある場合は、列間の差に基づいて計算されます。
