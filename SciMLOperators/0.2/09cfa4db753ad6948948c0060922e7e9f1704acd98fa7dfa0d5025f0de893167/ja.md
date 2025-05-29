```julia
⊗(ops)

```

遅延ペアワイズ・クロネッカー積、またはテンソル積演算子を `AbstractMatrix` および `AbstractSciMLOperator` サブタイプのために計算します。 `⊗(ops...)` を呼び出すことは `Base.kron(ops...)` と同等です。完全なテンソル積演算子を形成することなく、高速な演算子評価が行われます。

```
TensorProductOperator(A, B) = A ⊗ B
TensorProductOperator(A, B, C) = A ⊗ B ⊗ C

(A ⊗ B)(u) = vec(B * reshape(u, M, N) * transpose(A))
```

ここで、`M = size(B, 2)`、および `N = size(A, 2)` です。
