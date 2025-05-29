```
JackknifeVector(f::Function, jks::JackknifeVector...)

`jks`に`f`を適用することでJackknifeVectorの観測量を構築します。
例えば、`JackknifeVector(mean, jk1, jk2, jk3)`は`jk1`、`jk2`、および`jk3`の平均のJackknifeVector観測量を返します。
```
