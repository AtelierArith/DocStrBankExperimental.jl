```
kron_sum(F::AbstractMatrix, k::Int)
```

次数 k のクロネッカー和を計算します。定義は次の通りです：

$$
    F ⊕ F ⊕ ... ⊕ F := F ⊗ I ⊗ ... ⊗ I + I ⊗ F ⊗ I ⊗ ... ⊗ I + ... + I ⊗ ... ⊗ I ⊗ F
$$

ここで、各項は `k` 個の積を持ち、合計で `k` 個の和があり、`I` は次数 `n` の単位行列です。

### 例

次のようになります：

  * $$
    k = 1: F
    $$
  * $$
    k = 2: F ⊗ I + I ⊗ F
    $$
  * $$
    k = 3: F ⊗ I ⊗ I + I ⊗ F ⊗ I + I ⊗ I ⊗ F
    $$

```jldoctest
julia> F = sparse([0 1; -1 0.])
2×2 SparseMatrixCSC{Float64,Int64} with 2 stored entries:
  [2, 1]  =  -1.0
  [1, 2]  =  1.0

julia> kron_sum(F, 1) == F
true

julia> I2 = I(2)
IdentityMultiple{Float64} of value 1.0 and order 2

julia> kron_sum(F, 2) == kron(F, I2) + kron(I2, F)
true

julia> kron_sum(F, 3) == sum(reduce(kron, X) for X in [[F, I2, I2], [I2, F, I2], [I2, I2, F]])
true
```
