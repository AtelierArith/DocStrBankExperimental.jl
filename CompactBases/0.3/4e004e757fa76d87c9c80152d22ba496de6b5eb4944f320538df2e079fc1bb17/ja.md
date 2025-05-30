```
ShiftAndInvert(A, R[, σ=0])
```

固有値問題 $(\mat{A}-σ\mat{B})\vec{x} = \lambda\mat{B}\vec{x}$ に対応するシフトされた反転演算子を構築します。ここで、$\mat{B}$ は使用される `AbstractQuasiMatrix` `R` に依存する適切な演算子メトリックです。
