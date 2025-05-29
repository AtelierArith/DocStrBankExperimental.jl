```
RandomizedSystem(F::Union{System,AbstractSystem}, k::Integer;
        identity_block = true,
        compile = mixed)
```

与えられた $n × N$ システム `F` は、システム$\mathfrak{R}(F; k)(x) = A⋅F(x)$を構築します。ここで$A$は$k × N$行列です。`identity_block = true` の場合、$A$の最初の`k`列は単位行列を形成します。他のエントリはランダムな複素数です。詳細については、[^^SW05]の第13.5章を参照してください。

```
RandomizedSystem(F::Union{System,AbstractSystem}, A::Matrix{ComplexF64};
    identity_block = true,
    compile = mixed)
```

使用されるランダム化行列を明示的に提供します。`identity = true` の場合、`A` は `k × (n - k)` 行列でなければなりません。そうでない場合、`A` は `k × n` 行列でなければなりません。

[^SW05]: Sommese, A. J., & Wampler, C. W. (2005). The Numerical Solution of Systems of Polynomials Arising in Engineering and Science. World Scientific.
