```
solve_for_update(F::LUFactor, pos::Int64; getsol::Bool=false) -> SparseVector{Float64, Int64}
```

因子分解を更新する準備として転置された系を解きます。`pos`は次回の[`update`](@ref)呼び出しで置き換えられる因子化された行列の列インデックスを保持します。`getsol = true`の場合、右辺として単位ベクトルを用いた転置解からの解が返されます。そうでない場合は、更新のみが準備されます。
