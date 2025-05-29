```
LensTrace{T<:Real,N}
```

光学トレース内の交差点とそれに向かう光線セグメントを含みます。光線は、経路長、パワー、波長、交差点の数、ソース番号を持ち、これらはすべてこのクラスで直接アクセス可能です。

以下のアクセサメソッドがあります：

```julia
ray(a::LensTrace{T,N}) -> OpticalRay{T,N}
intersection(a::LensTrace{T,N}) -> Intersection{T,N}
power(a::LensTrace{T,N}) -> T
wavelength(a::LensTrace{T,N}) -> T
pathlength(a::LensTrace{T,N}) -> T
point(a::LensTrace{T,N}) -> SVector{N,T}
uv(a::LensTrace{T,N}) -> SVector{2,T}
sourcenum(a::LensTrace{T,N}) -> Int
nhits(a::LensTrace{T,N}) -> Int
```
