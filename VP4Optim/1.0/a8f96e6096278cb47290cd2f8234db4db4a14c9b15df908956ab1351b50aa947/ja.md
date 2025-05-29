```
f(mod::Model)
```

最小化される引数 `x` の関数 `f` を返します。これは、Optim.jl によって期待されるものです。

## 注意

  * 無名関数 `x -> ...` を返します（cf. [Optim.jl](https://github.com/JuliaNLSolvers/Optim.jl)）
  * [Bb!](@ref Bb!) に依存します。
