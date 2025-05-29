```
抽象型 InnerSolver
```

この型から継承される構造体は、内外反復における内問題を解決するために使用されます。

`InnerSolver` オブジェクトは NEP アルゴリズムに渡され、これを使用して関数 [`inner_solve`](@ref) の正しいバージョンをディスパッチします。既存の NEP ソルバーの実装を利用し、[`inner_solve`](@ref) はこれらのラッパーとして機能します。

# 例

提供された NEP に基づいて内ソルバーをディスパッチする [`DefaultInnerSolver`](@ref) があります。しかし、この例では [`nlar`](@ref) に対して PEP 用の [`IARInnerSolver`](@ref) を強制的に使用する方法を示します。

```julia-repl
julia> nep=nep_gallery("pep0", 100);
julia> λ,v = nlar(nep, inner_solver_method=NEPSolver.IARInnerSolver(), neigs=1, num_restart_ritz_vecs=1, maxit=70, tol=1e-8);
julia> norm(compute_Mlincomb(nep,λ[1],vec(v)))
8.68118417430353e-9
```

関連項目: [`inner_solve`](@ref), [`DefaultInnerSolver`](@ref), [`NewtonInnerSolver`](@ref), [`PolyeigInnerSolver`](@ref), [`IARInnerSolver`](@ref), [`IARChebInnerSolver`](@ref), [`SGIterInnerSolver`](@ref), [`ContourBeynInnerSolver`](@ref)
