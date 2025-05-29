```
solve_for_update(F::LUFactor, newcol::SparseVector{Float64, Int64}; getsol::Bool=false) -> SparseVector{Float64, Int64}
```

因子分解を更新する準備として前方系を解きます。`newcol`は、次の[`update`](@ref)呼び出しで因子化された行列に挿入される列を保持します。`getsol = true`の場合、右辺`newcol`を用いた前方解法からの解が返されます。それ以外の場合は、更新のみが準備されます。
