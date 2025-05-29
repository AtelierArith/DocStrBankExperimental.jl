```
@pga3(T, ex)
@pga3(ex)
```

Macro generated via `SymbolicGA.@geometric_space` with signature `(3, 0, 1)`  and the following definitions:

  * ```julia
    embed(x) = x[1]::e1 + x[2]::e2 + x[3]::e3
    ```
  * ```julia
    magnitude2(x) = x ⦿ x
    ```
  * ```julia
    point(x) = embed(x) + 1.0::e4
    ```

nothing
