```
@cga3(T, ex)
@cga3(ex)
```

Macro generated via `SymbolicGA.@geometric_space` with signature `(4, 1)`  and the following definitions:

  * ```julia
    embed(x) = x[1]::e1 + x[2]::e2 + x[3]::e3
    ```
  * ```julia
    magnitude2(x) = x ⦿ x
    ```
  * ```julia
    point(x) = (embed(x) + (0.5::Scalar ⟑ magnitude2(embed(x))) ⟑ n + n̄)::Vector
    ```
  * ```julia
    weight(X) = -X ⋅ n
    ```
  * ```julia
    unitize(X) = X / weight(X)
    ```
  * ```julia
    radius2(X) = (magnitude2(X) / magnitude2(X ∧ n))::Scalar
    ```
  * ```julia
    center(X) = (X ⟑ n) ⟑ X
    ```
  * ```julia
    distance(S, X) = unitize(S) ⋅ unitize(X)
    ```

Base.Docs.DocStr(svec("3D Conformal Geometric Algebra.\n\n!!! warning\n    This functionality is experimental and will likely be subject to change in the future.\n    It is not recommended for use beyond prototyping and playing around.\n"), nothing, Dict{Symbol, Any}(:typesig => Union{}, :module => SymbolicGA, :linenumber => 94, :binding => SymbolicGA.@cga3, :path => "/home/terasaki/.julia/packages/SymbolicGA/2XuTJ/src/spaces.jl"))
