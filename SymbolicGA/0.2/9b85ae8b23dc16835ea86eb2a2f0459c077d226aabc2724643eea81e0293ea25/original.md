```
@pga2(T, ex)
@pga2(ex)
```

Macro generated via `SymbolicGA.@geometric_space` with signature `(2, 0, 1)`  and the following definitions:

  * ```julia
    embed(x) = x[1]::e1 + x[2]::e2
    ```
  * ```julia
    magnitude2(x) = x ⦿ x
    ```
  * ```julia
    point(x) = embed(x) + 1.0::e3
    ```

nothing
