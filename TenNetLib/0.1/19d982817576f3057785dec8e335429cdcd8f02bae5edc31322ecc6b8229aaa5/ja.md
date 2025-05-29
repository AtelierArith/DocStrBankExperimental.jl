```
function measure(::Type{ElT} = ComplexF64, psi::MPS, opten::ITensor)
```

与えられた MPS `psi::MPS` の（複素数 / 実数）局所期待値（`::ComplexF64` / `::Float64`）を返します。演算子 `opten::ITensor` は単一サイト演算子でなければなりません。

`ElT = Float64` の場合、期待値が複素数であると警告が発生します！
