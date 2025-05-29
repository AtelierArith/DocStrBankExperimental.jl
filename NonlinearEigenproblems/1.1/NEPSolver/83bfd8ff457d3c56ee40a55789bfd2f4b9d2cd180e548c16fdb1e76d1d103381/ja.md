```
function IARChebInnerSolver(;tol=1e-13,maxit=80,starting_vector=:ones,
                            normalize_DEPs=true)
```

[`iar_chebyshev`](@ref) を使用して内部問題を解決します。キーワード引数のドキュメントについては [`IARInnerSolver`](@ref) を参照してください。

関連項目: [`IARInnerSolver`](@ref), [`InnerSolver`](@ref), [`inner_solve`](@ref)
