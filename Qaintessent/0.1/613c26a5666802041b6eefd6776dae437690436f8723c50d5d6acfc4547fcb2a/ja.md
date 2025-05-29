```
apply(ψ::Statevector, c::Circuit{N}) where {N}
```

は、`c.cgc`の回路ゲートを`N`量子ビットの状態ベクトル`ψ`に適用した後、`c.meas`の測定演算子からの期待値のリストを返します。
