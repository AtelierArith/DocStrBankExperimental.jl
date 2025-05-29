```
improved_estimator(model::Ising, T::Real, Js::AbstractArray, sw::SWInfo)
```

クラスタ情報 `sw` を使用して、次の観測量を `Dict{String, Any}` として返します。

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
  * `"Clustersize^2"`

      * $$
        \sum_c r_c^2
        $$

        , ここで $r_c$ は $c$-番目のクラスタのサイズ密度
  * `"Clustersize^4"`

      * $$
        \sum_c r_c^4
        $$
  * `"Clustersize^2 Clustersize^2"`

      * $$
        \sum_{c\ne c'} r_c^2 r_{c'}^2
        $$
