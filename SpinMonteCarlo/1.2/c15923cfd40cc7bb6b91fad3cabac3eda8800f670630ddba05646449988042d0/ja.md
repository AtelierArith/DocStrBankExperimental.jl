```
simple_estimator(model::Ising, T::Real, Js::AbstractArray)
```

次の観測量を `Dict{String, Any}` として返します

# 観測量

  * `"Energy"`

      * エネルギー密度
  * `"Energy^2"`

      * エネルギー密度の二乗
  * `"Magnetization"`

      * 磁化密度
  * `"|Magnetization|"`

      * 磁化密度の絶対値
  * `"Magnetization^2"`

      * 磁化密度の二乗
  * `"Magnetization^4"`

      * 磁化密度の四乗
