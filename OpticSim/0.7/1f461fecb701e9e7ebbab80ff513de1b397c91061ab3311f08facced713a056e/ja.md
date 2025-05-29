```
OpticalRay{T,N} <: AbstractRay{T,N}
```

パワー、波長、光路長を持つ光線。

**注意**: モンテカルロ積分を使用して検出器での正確な結果を得るため、すべての光線は本質的にパワー = 1 で検出器に当たります。また、反射/透過を正しく一致させるために、任意のインターフェースでいくつかの光線が捨てられます。検査目的のために、`OpticalRay`の`power`フィールドにおいて光線の「瞬時の」パワーも追跡します。

```julia
OpticalRay(ray::Ray{T,N}, power::T, wavelength::T, opl=zero(T))
OpticalRay(origin::SVector{N,T}, direction::SVector{N,T}, power::T, wavelength::T, opl=zero(T))
```

次のアクセサーメソッドがあります：

```julia
ray(r::OpticalRay{T,N}) -> Ray{T,N}
direction(r::OpticalRay{T,N}) -> SVector{N,T}
origin(r::OpticalRay{T,N}) -> SVector{N,T}
power(r::OpticalRay{T,N}) -> T
wavelength(r::OpticalRay{T,N}) -> T
pathlength(r::OpticalRay{T,N}) -> T
sourcepower(r::OpticalRay{T,N}) -> T
nhits(r::OpticalRay{T,N}) -> Int
sourcenum(r::OpticalRay{T,N}) -> Int
```
