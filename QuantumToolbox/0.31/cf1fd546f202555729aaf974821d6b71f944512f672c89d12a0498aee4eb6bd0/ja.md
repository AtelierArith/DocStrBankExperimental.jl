```
struct BlockDiagonalForm
```

行列のブロック対角形式を格納するための型です。

# フィールド

  * `B::DT`: ブロック対角行列。スパース行列または[`QuantumObject`](@ref)であることができます。
  * `P::DT`: 順列行列。スパース行列または[`QuantumObject`](@ref)であることができます。
  * `blocks::AbstractVector`: ブロック対角行列のブロック。
  * `block_sizes::AbstractVector`: ブロックのサイズ。
