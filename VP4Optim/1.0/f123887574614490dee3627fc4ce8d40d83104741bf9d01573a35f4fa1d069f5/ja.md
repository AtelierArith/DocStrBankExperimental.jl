```
fg!(mod::Model)
```

関数 `fg!` を三つの引数 `(F, G, x)` で返します。これは Optim.jl によって期待されるものです。

## 注記

  * 無名関数 `(F, G, x) -> ...` を返します（cf. [Optim.jl](https://github.com/JuliaNLSolvers/Optim.jl)）
  * [Bb!](@ref Bb!) と [∂Bb!](@ref ∂Bb!) に依存します。
