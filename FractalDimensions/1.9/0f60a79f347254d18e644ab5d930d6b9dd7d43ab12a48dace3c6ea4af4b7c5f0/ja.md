```
linear_regions(x, y; dxi, tol) → lrs, tangents
```

[`LargestLinearRegion`](@ref)で説明されているアルゴリズムを適用し、線形領域に対応する`x`のインデックス、`lrs`、および各領域での`tangents`（各累積領域での二次線形回帰を介して得られる）を返します。したがって、`lrs`は`UnitRange`のベクトルです。
