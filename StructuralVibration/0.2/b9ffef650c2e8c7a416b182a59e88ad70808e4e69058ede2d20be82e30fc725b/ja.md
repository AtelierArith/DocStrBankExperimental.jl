```
GaussianPulse(F, tstart, duration, fc)
```

ガウスパルス励起信号を定義する構造体

**フィールド**

  * `F::Real`: 力の振幅 [N]
  * `tstart::Real`: 励起の開始時間 [s]
  * `duration::Real`: 励起の持続時間 [s]
  * `fc::Real`: パルスの中心周波数 [Hz]
  * `precision::Real`: パルスの精度 (デフォルト = 4.)

**注意**

精度パラメータはパルスの標準偏差をキャリブレーションし、持続時間 = n x σ となるようにします。n = 1.96 の場合、ガウス分布の信頼区間は 95% です。これを行うために、t = duration = n x σ のときに F x exp(-0.5*(t - duration/2)^2/sigma^2) = 10^(-precision) となるように n を計算します。
