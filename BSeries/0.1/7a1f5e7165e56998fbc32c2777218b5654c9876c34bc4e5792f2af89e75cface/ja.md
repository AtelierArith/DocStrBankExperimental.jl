```
is_energy_preserving(series_integrator)::Bool
```

この関数は、時間積分法のB系列 `series_integrator` がハミルトン系に対してエネルギー保存的であるかどうかをチェックします - `series_integrator` の[`order`](@ref)まで。

# 参考文献

このコードは次の文献の定理2に基づいています。

  * Elena Celledoni, Robert I. McLachlan, Brynjulf Owren, and G. R. W. Quispel. "Energy-preserving integrators and the structure of B-series." Foundations of Computational Mathematics 10 (2010): 673-693. [DOI: 10.1007/s10208-010-9073-1](https://link.springer.com/article/10.1007/s10208-010-9073-1)
