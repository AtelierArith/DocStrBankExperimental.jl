```
simple_estimator(model::Clock, T::Real, Js::AbstractArray)
simple_estimator(model::XY, T::Real, Js::AbstractArray)
```

次の観測量を `Dict{String, Any}` として返します

# 観測量

  * `"Energy"`

      * スピン（サイト）あたりのエネルギー
  * `"Energy^2"`
  * `"|Magnetization|"`

      * スピンあたりの総磁化の絶対値（秩序パラメータ）
  * `"|Magnetization|^2"`
  * `"|Magnetization|^4"`
  * `"Magnetization x"`

      * スピンあたりの総磁化の x 成分（秩序パラメータ）
  * `"|Magnetization x|"`
  * `"Magnetization x^2"`
  * `"Magnetization x^4"`
  * `"Magnetization y"`

      * スピンあたりの総磁化の y 成分（秩序パラメータ）
  * `"|Magnetization y|"`
  * `"Magnetization y^2"`
  * `"Magnetization y^4"`
  * `"Helicity Modulus x"`
  * `"Helicity Modulus y"`
