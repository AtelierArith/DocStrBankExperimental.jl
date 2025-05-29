```
make_compute_imp_tendency(model::EnergyHydrology)
```

関数 `make_compute_imp_tendency` の拡張で、統合土壌エネルギーおよび熱方程式を含み、相変化を考慮しています。

このバージョンの関数は、現在暗黙的にステップを踏んでいる唯一の量である `Y.soil.ϑ_l` の PDE の右辺を計算します。

この関数は、Differential Equations.jl と連携して動作するように書かれています。
