```
square_up(F::Union{System, AbstractSystem}; identity_block = true, compile = compile = mixed)
```

[`RandomizedSystem`](@ref) $\mathfrak{R}(F(x); N)$ を作成します。ここで、$N$ は `F` の変数の数です。
