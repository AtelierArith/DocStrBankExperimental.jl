```
EmpiricalVariogramSurface(data, var₁, var₂=var₁;
                          normal=Vec(0,0,1), nangs=50,
                          ptol=0.5u"m", dtol=0.5u"m",
                          [options])
```

与えられた `normal` 方向に対して、変数 `var₁` と `var₂` の (クロス)バリオグラムを対応する変動平面に沿ってすべての方向で推定します。

オプションで、平面分割のための長さ単位での許容誤差 `ptol`、方向分割のための長さ単位での許容誤差 `dtol`、平面内の角度の数 `nangs` を指定し、`options` を基礎となる [`EmpiricalVariogram`](@ref) に渡します。
