```
Reflection(α; through_pt=nothing)
Reflection(vec::Point; through_pt=nothing)
Reflection(p1::Point, p2::Point)
```

線に対する反射を構築します。

線は、2つの点 `p1, p2` で指定することも、方向と線が通過する点 `through_pt` で指定することもできます。方向はベクトルまたは正の x 軸との角度（単位は受け入れられます; 単位なし => ラジアン）であり、`through_pt` はデフォルトで原点です。
