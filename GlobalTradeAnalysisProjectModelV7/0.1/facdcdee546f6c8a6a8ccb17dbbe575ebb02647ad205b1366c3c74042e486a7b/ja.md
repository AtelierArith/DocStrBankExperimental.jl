```
build_model!(mc; max_iter=50, constr_viol_tol=1e-8, bound_push=1e-15)
```

提供されたモデルコンテナ（`mc`）内に空のIpoptモデルを持つGTAPモデルを構築します。この関数は通常、ユーザーによって呼び出されることはなく、代わりに`generate_initial_model()`によって呼び出されます。ただし、ユーザーがモデルを変更したい場合は、この関数を拡張することができます。

### 引数:

  * `mc`: モデルコンテナ

### オプション引数:

  * `max_iter`: 最大反復回数
  * `constr_viol_tol`: 制約満足の精度
  * `bound_push`: 制約境界からの初期値の必須移動

### 戻り値:

何も返さず、`mc`オブジェクトを修正し、既存の`model`要素を追加します。

### 例:

`julia build_model!(mc)`
