```
EmpiricalTransiogramSurface(data, var;
                            normal=Vec(0,0,1), nangs=50,
                            ptol=0.5u"m", dtol=0.5u"m",
                            [options])
```

与えられた `normal` 方向に対して、変数 `var` のトランジオグラムを対応する変動平面のすべての方向に沿って推定します。

オプションで、平面分割の長さ単位での許容誤差 `ptol`、方向分割の長さ単位での許容誤差 `dtol`、平面内の角度の数 `nangs` を指定し、`options` を基盤となる [`EmpiricalTransiogram`](@ref) に渡します。
