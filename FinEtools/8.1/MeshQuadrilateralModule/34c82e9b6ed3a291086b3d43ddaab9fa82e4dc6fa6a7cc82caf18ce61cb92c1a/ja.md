```
Q8annulus(rin::T, rex::T, nr::IT, nc::IT, Angl::T) where {T<:Number, IT<:Integer}
```

環状セグメントのメッシュ。

原点を中心とした環状セグメントのメッシュで、内部半径`rin`、外部半径`rex`、および展開角度`Angl`を持ちます。放射方向と周方向にそれぞれ`nr`、`nc`の要素に分割されています。
