```
DGSEM(; RealT=Float64, polydeg::Integer,
        surface_flux=flux_central,
        surface_integral=SurfaceIntegralWeakForm(surface_flux),
        volume_integral=VolumeIntegralWeakForm(),
        mortar=MortarL2(basis))
```

ポリノミアルの次数 `polydeg` を持つ [`LobattoLegendreBasis`](@ref) を使用して、不連続ガレルキンスペクトル要素法 (DGSEM) を作成します。
