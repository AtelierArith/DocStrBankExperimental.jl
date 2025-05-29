```
H8elliphole(
    xradius::T,
    yradius::T,
    L::T,
    H::T,
    T::T,
    nL::IT,
    nH::IT,
    nW::IT,
    nT::IT,
) where {T<:Number, IT<:Integer}
```

楕円形の穴が開いた長方形プレートの1/4のメッシュ。

`xradius`,`yradius` = 楕円の半径、`L`,`H` = プレートの寸法、`Th` = プレートの厚さ、`nL`,`nH` = プレートの側面に沿ったエッジの数；これは楕円形の穴の周囲に沿ったエッジの数でもあります。`nW` = 残りの直線エッジ（穴から放射方向への）に沿ったエッジの数、
