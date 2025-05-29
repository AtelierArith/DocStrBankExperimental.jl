```julia
MultipleDomain(T=Float64, C=PlanarAr;
    age::AbstractVector,
    age_sigma::AbstractVector,
    fraction_experimental::AbstractVector,
    fraction_experimental_sigma::Number=T(0.01),
    tsteps_experimental::AbstractVector,
    Tsteps_experimental::AbstractVector,
    fit::AbstractVector,
    offset::Number = zero(T),
    fuse::Bool = true,
    volume_fraction::AbstractVector,
    r::Number = 100,
    dr::Number = one(T),
    K40::Number = 16.34, 
    agesteps::AbstractRange,
    tsteps::AbstractRange=reverse(agesteps),
)
```

観測されたアルゴン放出スペクトル、脱ガススケジュールに基づいて `MultipleDomain` 拡散クロノメーターを構築します。ドメインは `PlanarAr` または `SphericalAr` クロノメーターで表されます。

ドメインの拡散性と体積パラメータは、放出スペクトルを別々にフィッティングして得られたベクトル `Ea` [kJ/mol]、`lnD0a2` [log(1/s)]、および `volume_fraction` [単位なし] として供給する必要があります（前者の2つは `MDDiffusivity` オブジェクトとして）。

参照: `MDDiffusivity`, `PlanarAr`, `SphericalAr`, `degas!`
