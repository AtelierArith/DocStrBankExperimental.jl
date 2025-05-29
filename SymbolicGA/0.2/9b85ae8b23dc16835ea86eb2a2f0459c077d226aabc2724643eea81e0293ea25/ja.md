```
@pga2(T, ex)
@pga2(ex)
```

`SymbolicGA.@geometric_space`を介して生成されたマクロで、シグネチャは `(2, 0, 1)` で、以下の定義があります：

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
