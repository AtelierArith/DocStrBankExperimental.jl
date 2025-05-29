```
function measure(::Type{ElT} = ComplexF64, psi::MPS, optens::Vector{ITensor})
```

与えられた MPS `psi::MPS` に対する与えられた単一サイト演算子のベクトル (`optens::Vector{ITensor}`) の（複素数 / 実数）マルチサイト期待値 (`::ComplexF64` / `::Float64`) を返します。

`ElT = Float64` の場合、期待値が複素数であると警告が発生します！
