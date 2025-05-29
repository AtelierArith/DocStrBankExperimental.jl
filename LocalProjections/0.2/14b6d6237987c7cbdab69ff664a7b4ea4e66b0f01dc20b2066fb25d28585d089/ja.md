```
irf(r::LocalProjectionResult, yname::VarName, xwname::VarName; lag::Int=0)
```

推定結果 `r` に基づいて、変数 `xwname` に対する結果変数 `yname` の [`ImpulseResponse`](@ref) を返します。`lag` が指定されていない場合、`xwname` は同時的であると見なされます。
