```
make_compute_exp_tendency(model::SoilCO2Model)
```

`make_compute_exp_tendency` 関数の拡張で、soilco2 方程式用です。この関数は、PDE の `C` の右辺全体を計算し、その値で `dY.soil.C` をインプレースで更新する関数を作成して返します。これらの量は明示的にステップされます。

これは、Differential Equations.jl と連携して動作するように書かれています。
