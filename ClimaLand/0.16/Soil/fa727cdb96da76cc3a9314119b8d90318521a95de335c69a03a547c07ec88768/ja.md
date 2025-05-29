```
make_compute_imp_tendency(model::RichardsModel)
```

リチャードソン-リチャーズ方程式のための関数 `make_compute_imp_tendency` の拡張です。

この関数は、PDEの右辺全体を `ϑ_l` のために計算し、その値で `dY.soil.ϑ_l` をインプレースで更新する関数を作成して返します。
