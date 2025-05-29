`LBFGS(domainType::Type,dim_in::Tuple, M::Integer)`

`LBFGS(dim_in::Tuple, M::Integer)`

`LBFGS(x::AbstractArray, M::Integer)`

メモリ `M` を持つ制限付きメモリ BFGS `LinearOperator` を構築します。`LBFGS` のメモリは、現在の反復変数と勾配（`x`、`grad`）および以前のもの（`x_prev` と `grad_prev`）が必要な `update!` 関数を使用して更新できます：

```
julia> L = LBFGS(Float64,(4,),5)
LBFGS  ℝ^4 -> ℝ^4

julia> update!(L,x,x_prev,grad,grad_prev); # メモリを更新

julia> d = L*grad; # 新しい方向を計算

```

`reset!(L)` を使用してオペレーターのメモリをキャンセルします。
