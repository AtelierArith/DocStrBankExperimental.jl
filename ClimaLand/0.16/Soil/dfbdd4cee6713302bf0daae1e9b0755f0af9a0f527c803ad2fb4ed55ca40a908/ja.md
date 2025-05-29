```
make_compute_exp_tendency(model::EnergyHydrology)
```

関数 `make_compute_exp_tendency` の拡張で、統合土壌エネルギーおよび熱方程式を含み、相変化を考慮しています。

この関数は、`Y.soil.ϑ_l, Y.soil.θ_i, Y.soil.ρe_int` の PDE の右辺全体を計算する関数を作成し、これらの値で `dY.soil` をその場で更新して返します。これらの量はすべて明示的にステップされます。

これは、Differential Equations.jl で動作するように書かれています。
