```
cond(A::MatrixWorkspace,
     d_l::Union{Nothing,Vector{<:Real}} = nothing,
     d_r::Union{Nothing,Vector{<:Real}} = nothing)
```

`diag(d_l) * A * diag(d_r)`の無限ノルムに関する条件数を計算します。`d_l`または`d_r`が`nothing`の場合は、すべての要素が1のベクトルが使用されます。`size(A) == (1,1)`の場合は、逆行列のノルムのみが返されます。
