```
stieltjes(N::Int,nodes_::AbstractVector{<:Real},weights_::AbstractVector{<:Real};removezeroweights::Bool=true)
```

Stieltjes手続き–-ノードと重みが与えられたとき、関数は対応する離散直交多項式の最初の`N`再帰係数を生成します。

ゼロ重みを削除する必要がある場合は、ブール値`removezeroweights`を`true`に設定してください。
