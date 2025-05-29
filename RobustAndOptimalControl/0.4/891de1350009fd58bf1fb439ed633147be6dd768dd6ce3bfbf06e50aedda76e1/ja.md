```
mo_sys_from_particles(P::AbstractStateSpace; sparse = nparticles(P.A) > 500)
```

`Particles`係数を持つ状態空間モデルを、`P`と同じ数の入力を持つ単一の状態空間モデルに変換しますが、出力および状態の次元は`nparticles(P.A)`倍になります。

`sparse`がtrueの場合、結果のモデルはスパースな`A`、`C`、および`D`行列を持つ`HeteroStateSpace`になります。
