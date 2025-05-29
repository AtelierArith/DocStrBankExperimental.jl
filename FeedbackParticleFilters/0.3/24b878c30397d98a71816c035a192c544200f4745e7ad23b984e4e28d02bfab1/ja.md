```
update!(eq::GainEquation)
```

ゲイン方程式 `eq` を更新し、それに含まれるすべての情報が自己整合的であるようにします。

```
update!(eq::GainEquation, ens::ParticleRepresentation)
```

アンサンブル `ens` からの新しい情報を取り入れて、ゲイン方程式 `eq` を更新します。
