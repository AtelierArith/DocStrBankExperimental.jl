```
Q4elliphole(
    xradius::T,
    yradius::T,
    L::T,
    H::T,
    nL::IT,
    nH::IT,
    nW::IT,
) where {T<:Number, IT<:Integer}
```

楕円形の穴が開いた長方形プレートの1/4のメッシュ。

`xradius`,`yradius` = 楕円の半径、`L,H`= プレートの寸法、`nL,nH`= プレートの側面に沿ったエッジの数; これは楕円形の穴の周囲に沿ったエッジの数でもあります。`nW`= 残りの直線エッジ（穴から長さの方向に向かって）に沿ったエッジの数、
