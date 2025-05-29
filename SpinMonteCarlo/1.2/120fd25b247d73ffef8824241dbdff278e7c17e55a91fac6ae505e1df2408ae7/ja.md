```
simple_estimator(model::AshkinTeller, T::Real, Jsigma, Jtau, K)
```

次の観測量を `Dict{String, Any}` として返します。

# 観測量

  * `"Energy"`

      * エネルギー密度
  * `"Energy^2"`

      * エネルギー密度の二乗
  * `"|Magnetization|"`

      * 磁化密度の絶対値、$|m| = \sqrt{ (\sum_i \sigma_i )^2 + (\sum_i \tau_i)^2 } / N$
  * `"|Magnetization|^2"`

      * 磁化密度の二乗
  * `"|Magnetization|^4"`

      * 磁化密度の四乗
  * `"Magnetization sigma"`

      * 磁化密度（シグマスピン）
  * `"|Magnetization sigma|"`
  * `"Magnetization sigma^2"`
  * `"Magnetization sigma^4"`
  * `"Magnetization tau"`

      * 磁化密度（タウスピン）
  * `"|Magnetization tau|"`
  * `"Magnetization tau^2"`
  * `"Magnetization tau^4"`
