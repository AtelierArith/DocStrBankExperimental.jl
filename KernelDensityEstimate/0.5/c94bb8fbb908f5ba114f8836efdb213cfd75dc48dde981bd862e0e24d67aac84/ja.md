```julia
kde!(points)
kde!(points, ks)
kde!(points, ks, addop)
kde!(points, ks, addop, diffop)

```

`points`を中心、バンド幅`ks`を使用してBallTreeDensityオブジェクトを構築します。
