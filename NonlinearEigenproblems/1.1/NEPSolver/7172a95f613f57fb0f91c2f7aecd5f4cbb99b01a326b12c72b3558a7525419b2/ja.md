```
struct DefaultInnerSolver <: InnerSolver
```

提供されたNEPのタイプに基づいて[`inner_solve`](@ref)のバージョンをディスパッチします。この関数は、推奨されるソルバーを自動的に検出しようとします。

参照: [`InnerSolver`](@ref), [`inner_solve`](@ref)
