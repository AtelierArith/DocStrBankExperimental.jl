```
 approx(psd_model, f0, fM, n_components=20, var=1.0; basis_function="SHO")
```

基底関数の合計を用いてPSDを近似し、共分散関数を形成します。

# 引数

  * `psd_model::PowerSpectralDensity`: PSDのモデル
  * `f0::Real`: 最低周波数
  * `fM::Real`: 最高周波数
  * `n_components::Integer=20`: 使用する基底関数の数
  * `var::Real=1.0`: プロセスの分散、PSDの積分
  * `basis_function::String="SHO"`: 使用する基底関数、"SHO"または"DRWCelerite"

# 戻り値

  * `covariance::SumOfSemiSeparable`: 共分散関数

# 例

```julia
using Pioran
𝓟 = SingleBendingPowerLaw(1.0, 1.0, 2.0)
𝓡 = approx(𝓟, 1e-4, 1e-1, 30, 2.31,basis_function="SHO")
```
