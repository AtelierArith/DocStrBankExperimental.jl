```
ColumnHermite{T<:Integer,M<:AbstractMatrix{T}}
```

整数行列 `A` をその行スタイルのエルミート標準形 `H`（下三角行列）と、`H == A*U` または同等に `A == H/U` となるユニモジュラー行列 `U` に分解した結果を説明します。
