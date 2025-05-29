```
kron_sandwich(F, n, k1, k2)
```

`A ⊗ F ⊗ C` を計算します。ここで `A = I^{⊗ k1}` および `C = I^{⊗ k2}` であり、`I` は次元 `n` の単位行列で、単位行列の `k1` 回および `k2` 回のクロネッカー積の間に `F` が入ります。

### 入力

  * `F`  – 行列
  * `n`  – 整数、単位行列の次元
  * `k1` – 非負整数
  * `k2` – 非負整数

### 出力

クロネッカー積 `I^{⊗ k1} ⊗ F ⊗ I^{⊗ k2}` を出力します。`F` がスパースの場合はスパース行列として表現されます。

### 例

```jldoctest
julia> F = sparse([0 1; -1 0.])
2×2 SparseMatrixCSC{Float64,Int64} with 2 stored entries:
  [2, 1]  =  -1.0
  [1, 2]  =  1.0

julia> Q = kron_sandwich(F, 2, 2, 2);

julia> size(Q)
(32, 32)

julia> I2 = I(2)
IdentityMultiple{Float64} of value 1.0 and order 2

julia> Q == reduce(kron, [I2, I2, F, I2, I2])
true
```
