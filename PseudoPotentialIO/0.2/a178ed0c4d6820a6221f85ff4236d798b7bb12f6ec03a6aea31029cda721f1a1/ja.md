```julia
projector_fourier(
    psp::PseudoPotentialIO.AbstractPsP,
    l::Integer,
    n::Integer
) -> Any

```

`n`番目の非局所Kleinman-Bylander投影子が、逆空間点`q`で角運動量`l`で評価されます。

```julia
projector_fourier(psp, l, n)
```

[`packages/PseudoPotentialIO/YkY3g/src/psp/hgh.jl:144`](file:///home/terasaki/.julia/packages/PseudoPotentialIO/YkY3g/src/psp/hgh.jl)で定義されています。

```julia
projector_fourier(psp, l, n; tol)
```

[`packages/PseudoPotentialIO/YkY3g/src/psp/numeric.jl:137`](file:///home/terasaki/.julia/packages/PseudoPotentialIO/YkY3g/src/psp/numeric.jl)で定義されています。

```julia
projector_fourier(psp, l, n)
```

[`packages/PseudoPotentialIO/YkY3g/src/psp/psp.jl:240`](file:///home/terasaki/.julia/packages/PseudoPotentialIO/YkY3g/src/psp/psp.jl)で定義されています。
