```
run_path_sim(CH::AbstractChart; maxiter)
run_path_sim(CH::MultipleControlChart; maxiter)
```

制御チャート `CH` のためのラン長パスをシミュレートし、Phase II オブジェクトから新しいデータをサンプリングします。

### 入力

  * `CH::AbstractChart` - 制御チャート。
  * `maxiter::Real` - ラン長の最大値。デフォルトは `min(maxrl(CH), 10*get_nominal_value(CH))` です。

### 戻り値

  * 制御チャートのシミュレートされた値を含むベクター。
