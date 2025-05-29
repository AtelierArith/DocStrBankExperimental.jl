```
apply(ρ::DensityMatrix, c::Circuit{N}) where {N}
```

N量子ビット密度行列`ρ`に対して、回路ゲート`c.cgc`を適用した後、`c.meas`の測定演算子から期待値のリストを計算します。
