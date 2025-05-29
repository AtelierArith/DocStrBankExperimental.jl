```
ionizationcrosssection(z::Int, shell::Int, energy::AbstractFloat, ::Type{Bote2009})
ionizationcrosssection(ass::AtomicSubShell, energy::AbstractFloat, ty::Type{<:NeXLAlgorithm}=Bote2009)
```

指定されたAtomicSubShellと電子エネルギー（eV単位）に対する絶対イオン化断面積（cm²/e⁻）を計算します。

例:

```
julia> (/)(map(e->NeXLCore.ionizationcrosssection(n"Fe K",e),[10.0e3,20.0e3])...)
0.5672910174711278
```
