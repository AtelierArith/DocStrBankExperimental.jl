```
T6annulus(
    rin::T,
    rex::T,
    nr::IT,
    nc::IT,
    angl::T,
    orientation::Symbol = :a,
) where {T<:Number, IT<:Integer}
```

環状セグメントのメッシュ。

内部半径 `rin`、外部半径 `rex`、および展開角 `angl`（ラジアン単位）を持つ、原点を中心とした環状セグメントのメッシュ。放射方向と円周方向にそれぞれ nr、nc の要素に分割されています。
