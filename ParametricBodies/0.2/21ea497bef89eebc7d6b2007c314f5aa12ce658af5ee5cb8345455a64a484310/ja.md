```
PlanarBody(curve::NurbsCurve;map)       # NurbsLocatorを作成します
PlanarBody(curve,lims::Tuple;T,map,mem) # HashedLocatorを作成します
```

`ζ₃=0`平面に`map`で定義されたParametricBodyを埋め込みます。`curve`は最小厚さ`thk=ϵ+√3/2`の平面体の平面形状を定義します。Lauber & Weymouth 2022を参照してください。速度は`dot(map)`からのみ定義されることに注意してください。
