```
function measure(::Type{ElT} = ComplexF64, psi::TTN, opstr::String, pos::Int)
```

与えられた演算子名（`opstr::String`）とサイトインデックス（`pos::Int`）に対して、与えられたTTN `psi::TTN`の（複素数/実数）局所期待値（`::ComplexF64` / `::Float64`）を返します。

`ElT = Float64`の場合、期待値が複素数であると警告を発します！
