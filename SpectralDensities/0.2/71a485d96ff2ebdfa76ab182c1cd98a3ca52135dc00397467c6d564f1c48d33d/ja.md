```
struct ExponentialCutoffSD{T <: AbstractSD} <: AbstractSD
```

ExponentialCutoffSDは、指数関数的な周波数カットオフを持つスペクトル密度を表します。これは、基礎となるスペクトル密度 `J` と周波数カットオフ `ωcutoff` によってパラメータ化されています。すなわち、

$$
J_\mathrm{exp}(\omega) = J(\omega)e^{-\omega/\omega_c}
$$

# フィールド

  * `J::T`: 基礎となるスペクトル密度。
  * `ωcutoff::Float64`: 周波数カットオフ。
