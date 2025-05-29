```julia
projector_coupling(
    psp::PseudoPotentialIO.AbstractPsP,
    l::Int64,
    n::Int64,
    m::Int64
) -> Any

```

`n`番目と`m`番目のプロジェクター間の角運動量`l`を持つプロジェクター結合定数。

```julia
projector_coupling(psp, l, n, m)
```

[`packages/PseudoPotentialIO/YkY3g/src/psp/psp.jl:402`](file:///home/terasaki/.julia/packages/PseudoPotentialIO/YkY3g/src/psp/psp.jl)で定義されています。
