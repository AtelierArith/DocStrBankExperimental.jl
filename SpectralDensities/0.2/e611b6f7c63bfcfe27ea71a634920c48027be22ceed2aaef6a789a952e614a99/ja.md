```
struct HardCutoffSD{T <: AbstractSD} <: AbstractSD
```

HardCutoffSDは、ハード周波数カットオフを持つスペクトル密度を表します。これは、基礎となるスペクトル密度 `J` と周波数カットオフ `ωcutoff` によってパラメータ化されています。すなわち、

$$
J_\mathrm{hard}(\omega) = J(\omega)\Theta(\omega_c - \omega)
$$

ここで、$\Theta$ はヘヴィサイドのθ関数です。

# フィールド

  * `J::T`: 基礎となるスペクトル密度。
  * `ωcutoff::Float64`: 周波数カットオフ。
