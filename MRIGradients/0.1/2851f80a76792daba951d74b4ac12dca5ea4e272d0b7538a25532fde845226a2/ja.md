```
apply_girf(g::GirfApplier, gradient_in, time_in, time_out, direction)

GIRFを適用して勾配を予測するための関数
これは1次元のみで行われます。複数の次元についてはこの関数を繰り返してください
```

# 引数

  * `g::GirfApplier` - GIRFデータを含むGirfApplier
  * `gradient_in` - time_inベクトルに対応する入力勾配波形
  * `time_in` - 入力勾配波形に対応する時間ベクトル
  * `time_out` - 希望する出力時間ベクトル（ダウンサンプリング）
  * `direction` - 使用するGIRFの方向（x,y,zなど...）

# 出力:

  * `grad_OUT_resampled` - ベクトル、GIRFが適用された勾配波形、`time_out`の時間点で。
