```
DG(; basis, mortar, surface_integral, volume_integral)
```

不連続ガレルキン法を作成します。もし [`basis isa LobattoLegendreBasis`](@ref LobattoLegendreBasis) の場合、これは [`DGSEM`](@ref) を作成します。
