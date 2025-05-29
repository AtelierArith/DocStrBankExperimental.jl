```
AsymExactPropagator{T, E} <: AbstractExactPropagator{T,E}
```

虚時間伝播子行列を対称形式を用いて表します

$$
B_l = e^{-\Delta\tau V_l} e^{-\Delta\tau K_l},
$$

ここで、$K_l$は厳密にオフ対角のホッピング行列であり、$V_l$は対角の全サイトエネルギー行列です。

# フィールド

  * `expmΔτV::Vector{E}`: 対角の指数化されたサイトエネルギー行列 $e^{-\Delta\tau V_l}.$ を表すベクトル。
  * `expmΔτK::Matrix{T}`: 指数化されたホッピング行列 $e^{-\Delta\tau K_l}.$
  * `exppΔτK::Matrix{T}`: 指数化されたホッピング行列 $e^{+\Delta\tau K_l}.$ の逆行列。
