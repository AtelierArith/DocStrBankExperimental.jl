```
@cga3(T, ex)
@cga3(ex)
```

`SymbolicGA.@geometric_space`を介して生成されたマクロで、シグネチャは`(4, 1)`であり、以下の定義があります：

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

Base.Docs.DocStr(svec("3Dコンフォーマル幾何代数。\n\n!!! 警告\n    この機能は実験的であり、将来的に変更される可能性があります。\n    プロトタイピングや遊び以外での使用は推奨されません。\n"), nothing, Dict{Symbol, Any}(:typesig => Union{}, :module => SymbolicGA, :linenumber => 94, :binding => SymbolicGA.@cga3, :path => "/home/terasaki/.julia/packages/SymbolicGA/2XuTJ/src/spaces.jl"))
