```
GenericHausdorff(inner_op, outer_op, weights = nothing)
```

内側の縮小 `inner_op` と外側の縮小 `outer_op` を用いた一般化されたハウスドルフ距離。オプションで、距離変換が適用される前に各軸に対して `weights` を使用することができます。

## 参考文献

Dubuisson, M-P; Jain, A. K., 1994. *A Modified Hausdorff Distance for Object-Matching*.

参照: [`Hausdorff`](@ref), [`ModifiedHausdorff`](@ref)
