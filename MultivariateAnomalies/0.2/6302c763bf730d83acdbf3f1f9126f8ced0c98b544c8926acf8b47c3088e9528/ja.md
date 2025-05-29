```
REC(D::AbstractArray, rec_threshold::Float64, temp_excl::Int = 0)
```

距離行列 `D` の半径 `rec_threshold` に該当する観測値（再発）の数をカウントします。再発としてカウントされるのは、`temp_excl` よりも近いステップは除外されます（デフォルト: `temp_excl = 5`）

Marwan, N., Carmen Romano, M., Thiel, M., & Kurths, J. (2007). 複雑系の分析のための再発プロット. Physics Reports, 438(5-6), 237–329. http://doi.org/10.1016/j.physrep.2006.11.001
