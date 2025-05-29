```julia
pseudo_cutoff_radius(
    psp::PseudoPotentialIO.AbstractPsP;
    f,
    tol
) -> Any

```

擬似ポテンシャルのカットオフ半径を見つけます。異なる量に対するカットオフ半径の削減の種類を決定するために関数 `f` を供給してください。量が `|f| < tol` に減衰する場合に切り捨てたい場合は `tol` を供給してください。

```julia
pseudo_cutoff_radius(psp; f, tol)
```

[`packages/PseudoPotentialIO/YkY3g/src/psp/psp.jl:389`](file:///home/terasaki/.julia/packages/PseudoPotentialIO/YkY3g/src/psp/psp.jl) で定義されています。
