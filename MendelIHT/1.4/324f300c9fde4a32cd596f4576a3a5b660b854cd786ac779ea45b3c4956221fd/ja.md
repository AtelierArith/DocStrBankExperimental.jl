```
loglikelihood(v::mIHTVariable)
```

`Y`を平均`μ`および精度行列`Γ`（逆共分散行列）に基づいて観測する際の対数尤度を計算します。

注意: この関数はストレージ変数`v.r_by_r1`および`v.r_by_r2`を変更します。
