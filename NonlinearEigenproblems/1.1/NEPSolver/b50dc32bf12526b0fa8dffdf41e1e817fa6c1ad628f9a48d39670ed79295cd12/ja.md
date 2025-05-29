```
struct ContourBeynInnerSolver <: InnerSolver
function ContourBeynInnerSolver(;tol=sqrt(eps(real(Float64))),
                                radius=:auto,N=1000)
```

[`contour_beyn`](@ref)を使用して、`radius`と`n`で指定された数の積分ノードを持つ内部問題を解決します。変数`radius`が`:auto`に設定されている場合、外部ソルバーによって指定された固有値近似を使用して、積分半径が自動的に選択されます。

参照: [`InnerSolver`](@ref), [`inner_solve`](@ref)
