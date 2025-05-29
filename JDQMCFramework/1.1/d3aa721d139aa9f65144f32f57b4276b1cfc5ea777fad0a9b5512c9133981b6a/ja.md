```
AsymChkbrdPropagator{T, E} <: AbstractChkbrdPropagator{T,E}
```

虚時間伝播子行列を対称形式を用いて表します

$$
B_l = e^{-\Delta\tau V_l} e^{-\Delta\tau K_l},
$$

ここで、$K_l$は厳密にオフダイアゴナルなホッピング行列であり、$V_l$は対角の全サイトエネルギー行列です。指数化されたホッピング行列$e^{-\Delta\tau K}$はチェッカーボード近似によって表されます。

# フィールド

  * `expmΔτV::Vector{E}`: 対角の指数化されたオンサイトエネルギー行列$e^{-\Delta\tau V_l}.$を表すベクトル。
  * `expmΔτK::CheckerboardMatrix{T}`: チェッカーボード近似によって表された指数化されたホッピング行列$e^{-\Delta\tau K_l}$。
