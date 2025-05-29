```
struct NleigsInnerSolver <: InnerSolver
function NleigsInnerSolver(;Σ= :auto,nodes =:auto, tol=1e-6 )
```

[`nleigs`](@ref) を使用して、シフト `nodes` と許容誤差 `tol` を持つ領域 `Σ` で内部問題を解決します。変数 `Σ` が `:auto` に設定されている場合、領域 `Σ` は固有値の近似を使用して設定されます。パラメータの説明については、[`nleigs`](@ref) を参照してください。

関連情報: [`InnerSolver`](@ref), [`inner_solve`](@ref)
