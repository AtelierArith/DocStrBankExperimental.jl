```
walkmap(
    spheres::AbstractVector{Sphere{D}}, extent::NTuple{D,<:Real},
    resolution::Real, probe_radius::Real = 0;
    boundaries::Symbol = :cut
) where D
```

与えられた`spheres`の構成に対して、`extent`の領域内で`walkmap`を生成します。望ましい`resolution`を指定します。正の`probe_radius`は、「プローブ」が有限のサイズを持つと仮定して、歩行可能な空間を制限します。

`boundaries`は、領域の境界を越える球体をどのように扱うかを定義するために`:cut`または`:wrap`に設定できます（もしあれば）。
