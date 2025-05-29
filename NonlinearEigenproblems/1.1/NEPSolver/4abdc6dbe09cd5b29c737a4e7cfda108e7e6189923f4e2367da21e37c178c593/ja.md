```
struct PolyeigInnerSolver <: InnerSolver
function PolyeigInnerSolver()
```

[`polyeig`](@ref) を使用して内部問題を解決することを指定します。これは、[`PEP`](@ref) タイプの NEP に対して意図されています。

関連情報: [`InnerSolver`](@ref), [`inner_solve`](@ref)
