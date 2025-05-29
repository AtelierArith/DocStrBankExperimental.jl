```
add_column!(C::UpdatableCholesky, A::AbstractMatrix)
```

行列 A の列を追加し、それに対応する行 A' を `UpdatableCholesky` 因子分解 C に追加します。複雑さは `O(m³ + n²m)` であり、ここで `n = size(C, 1)` および `m = size(A, 2)` です。
