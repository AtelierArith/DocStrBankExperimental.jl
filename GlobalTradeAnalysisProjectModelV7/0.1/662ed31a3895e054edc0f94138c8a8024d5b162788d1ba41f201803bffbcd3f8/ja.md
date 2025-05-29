```
    calculate_expenditure(; sets, data0, data1, parameters, max_iter=50, constr_viol_tol=1e-5, bound_push=1e-15)
```

シミュレーション後の効用（data1）における支出を元の価格（data0）で計算します。

### 引数:

  * `sets`: セットの辞書
  * `data0`: ベースラインソリューションからのデータの辞書
  * `data1`: シミュレーションソリューションからのデータの辞書
  * `parameters`: パラメータの辞書

### オプション引数:

  * `max_iter`: 最大反復回数
  * `constr_viol_tol`: 制約満足の精度
  * `bound_push`: 制約境界からの開始値の必須移動

### 戻り値:

支出のベクトル。
