```
getcluster(y::Vector{<:Real}, u::Real; runlength::Int=1)::Vector{Cluster}
```

ベクトル `y` からクラスタを抽出します。

閾値を超える値が *r* 個未満の非超過値で区切られている場合、それらは同じクラスタに属します。値 *r* は runlength パラメータに対応します。このアプローチは *runs declustering scheme* と呼ばれています（Coles, 2001 sec. 5.3.2 を参照）。

[`Cluster`](@ref) も参照してください。
