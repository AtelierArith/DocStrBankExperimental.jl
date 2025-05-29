```
ClimaLand.make_compute_jacobian(model::EnergyHydrology{FT}) where {FT}
```

EnergyHydrologyモデルのcompute_jacobian!関数を作成して返します。これは土壌液体水分量の寄与のみを更新します。

このヤコビ行列を後方オイラータイムステッパーで使用することは、Celia et al. (1990)の修正ピカールスキームを使用することと同等です。
