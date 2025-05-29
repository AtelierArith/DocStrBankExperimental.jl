```
function measure(::Type{ElT} = ComplexF64, psi::TTN, optens::Vector{ITensor})
```

与えられた単一サイト演算子のベクトル（`optens::Vector{ITensor}`）に対する与えられたTTN `psi::TTN`の（複素数/実数）マルチサイト期待値（`::ComplexF64` / `::Float64`）を返します。

`ElT = Float64`の場合、期待値が複素数であると警告を発します！
