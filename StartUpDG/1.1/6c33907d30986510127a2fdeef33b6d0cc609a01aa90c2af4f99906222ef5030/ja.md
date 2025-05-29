```
function inverse_trace_constant(rd::RefElemData)
```

参照要素上の逆トレース等式における次数依存定数を返します（Chan, Wang, Modave, Remacle, Warburton 2016による["GPU-accelerated dG methods on hybrid meshes"](https://doi.org/10.1016/j.jcp.2016.04.003)で報告されています）。

近似の次数に対する最大安定タイムステップの依存性を推定するために使用できます。
