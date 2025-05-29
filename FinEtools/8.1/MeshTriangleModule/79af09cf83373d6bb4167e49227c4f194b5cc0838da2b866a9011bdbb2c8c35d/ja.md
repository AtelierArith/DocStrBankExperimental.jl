```
T3circleseg(
    angle::T,
    radius::T,
    ncircumferentially::IT,
    nperradius::IT,
    orientation::Symbol = :a,
) where {T<:Number, IT<:Integer}
```

円のセグメントのメッシュ。

弧に対する角度はラジアンで`angle`です。向きについては`T3block`を参照してください。
