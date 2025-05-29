```
fgh!(mod::Model)
```

関数 `fgh!` を4つの引数 `(F, G, H, x)` で返します。これは Optim.jl によって期待されるものです。

## 注記

  * 匿名関数 `(F, G, H, x) -> ...` を返します（参照：[Optim.jl](https://github.com/JuliaNLSolvers/Optim.jl)）
  * [Bb!](@ref Bb!)、[∂Bb!](@ref ∂Bb!) および [∂∂Bb!](@ref ∂∂Bb!) に依存します。
