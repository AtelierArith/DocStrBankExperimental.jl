```julia
chi_function_fourier(
    psp::PseudoPotentialIO.AbstractPsP,
    l::Integer,
    n::Integer
) -> Any

```

角運動量 `l` での `n` 番目のカイ関数を逆空間点 `q` で評価したもの。

```julia
chi_function_fourier(psp, l, n; tol)
```

[`packages/PseudoPotentialIO/YkY3g/src/psp/numeric.jl:142`](file:///home/terasaki/.julia/packages/PseudoPotentialIO/YkY3g/src/psp/numeric.jl) で定義されています。

```julia
chi_function_fourier(psp, l, n)
```

[`packages/PseudoPotentialIO/YkY3g/src/psp/psp.jl:248`](file:///home/terasaki/.julia/packages/PseudoPotentialIO/YkY3g/src/psp/psp.jl) で定義されています。
