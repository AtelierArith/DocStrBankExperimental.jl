```
kron_id(n, k)
```

単位行列のk重クロネッカー積を計算します: `I ⊗ I ⊗ ... ⊗ I`、k回。

### 入力

  * `n` – 単位行列の次数（次元）を表す整数
  * `k` – 指数を表す整数

### 出力

次数 $n^k$ の単位行列と型 `Diagonal`。

### 例

```jldoctest
julia> kron_id(2, 2)
4×4 Diagonal{Float64,Array{Float64,1}}:
 1.0   ⋅    ⋅    ⋅
  ⋅   1.0   ⋅    ⋅
  ⋅    ⋅   1.0   ⋅
  ⋅    ⋅    ⋅   1.0
```
