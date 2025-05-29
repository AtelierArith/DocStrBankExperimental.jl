```
run_model!(model_container; max_iter=50, constr_viol_tol=1e-8, bound_push=1e-15)
```

モデル（model*container.model）を実行することで、次のステップを実行します：（1）すべての開始値をデータ（model*container.data）に見つかった値に設定します、（2）外生的として指定されたすべての変数を固定します（model*container.fixed）、（3）モデルを解きます、（4）すべての変数の値をデータ（model*container.data）にロードします。

### 引数:

  * `model_container`: モデルコンテナ

### オプション引数:

  * `max_iter`: 最大反復回数
  * `constr_viol_tol`: 制約満足の精度
  * `bound_push`: 制約境界からの開始値の必須移動
