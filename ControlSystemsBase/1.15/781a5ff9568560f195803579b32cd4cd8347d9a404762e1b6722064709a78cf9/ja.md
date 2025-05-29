```
S, PS, CS, T = gangoffour(P, C; minimal=true)
gangoffour(P::AbstractVector, C::AbstractVector; minimal=true)
```

植物 `P` を表す伝達関数とコントローラ `C` を表す伝達関数が与えられたとき、Gang-of-Four の4つの伝達関数を計算します。

  * `S = 1/(1+PC)` 感度関数
  * `PS = (1+PC)\P` 荷の摂動から測定信号への影響
  * `CS = (1+PC)\C` 測定ノイズから制御信号への影響
  * `T = PC/(1+PC)` 補完感度関数

`minimal=true` の場合、[`minreal`](@ref) がすべての伝達関数に適用されます。
