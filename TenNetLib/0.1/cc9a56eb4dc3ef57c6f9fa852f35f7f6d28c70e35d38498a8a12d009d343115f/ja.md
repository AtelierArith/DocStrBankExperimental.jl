```
struct OpString{T <: Number}
    coeff::T
    ops::Vector{Pair{String, Int}}
end
```

演算子文字列（対応する位置を持つ演算子名）と係数を保持します。

  * `coeff::T`: 演算子文字列の係数。
  * `ops::Vector{Pair{String, Int}}`: 位置と共に演算子名の文字列。
