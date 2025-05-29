```
SparseOpt <: PerformanceOpt

SparseOpt()
```

グリッド内のすべてのパディング値（デフォルトではゼロ）を無視する最適化フラグです。

低密度シミュレーションでは、使用されるセルのみが実行されるため、パフォーマンスが桁違いに向上する可能性があります。

次のように指定します：

```julia
ruleset = Ruleset(rule; opt=SparseOpt())
# または
output = sim!(output, rule; opt=SparseOpt())
```

`SparseOpt`は、このシミュレーションで最もよく示されます。灰色の領域は、隣接する領域が灰色でない部分に部分的にかかっている場合を除いて実行されません：

![SparseOpt demonstration](https://raw.githubusercontent.com/cesaraustralia/DynamicGrids.jl/media/complexlife_spareseopt.gif)
