```
packing_fraction(spheres::Vector{Sphere{D}}, extent::NTuple{D,Real}) where D
```

`spheres`のパッキング分数を`extent`の領域で評価します。この測定は、球が重なっている場合や領域の境界を越えている場合は正確ではありません。
