```
struct GaussianCutoffSD{T <: AbstractSD} <: AbstractSD
```

GaussianCutoffSDは、ガウス周波数カットオフを持つスペクトル密度を表します。これは、基礎となるスペクトル密度 `J` と周波数カットオフ `ωcutoff` によってパラメータ化されています。すなわち、

$$
J_\mathrm{gauss}(\omega) = J(\omega)e^{-\omega^2/\omega_c^2}
$$

# フィールド

  * `J::T`: 基礎となるスペクトル密度。
  * `ωcutoff::Float64`: 周波数カットオフ。
