```
η([ty::Type{<:BackscatterCoefficient},] mat::Material, e0::Float64)::Float64 =
```

材料のためのバックスキャッタ係数を、Armstrongの1991年のアルゴリズムを使用して計算します。

@incollection{armstrong1991quantitative,   title={Quantitative elemental analysis of individual microparticles with electron beam instruments},   author={Armstrong, John T},   booktitle={Electron probe quantitation},   pages={261–315},   year={1991},   publisher={Springer} }
