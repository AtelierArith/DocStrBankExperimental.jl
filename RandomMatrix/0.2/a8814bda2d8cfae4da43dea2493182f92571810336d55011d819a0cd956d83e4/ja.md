```julia
randPermutation(n; fix) 
```

  * `n` : 次元
  * `fix` : キーワード引数で、デフォルトは `fix = 0` に設定されています。`fix = x` の場合、`randPermutation(n,x)` は少なくとも `x` 個の固定点を持ちます。

# 例

ランダムな 5×5 の置換行列を生成します。

```julia
randPermutation(5)

5×5 SparseArrays.SparseMatrixCSC{Int8, Int64} with 5 stored entries:
 ⋅  ⋅  ⋅  ⋅  1
 ⋅  1  ⋅  ⋅  ⋅
 1  ⋅  ⋅  ⋅  ⋅
 ⋅  ⋅  1  ⋅  ⋅
 ⋅  ⋅  ⋅  1  ⋅
```

少なくとも 7 個の固定点を持つランダムな 10×10 の置換行列を生成します。

```julia
randPermutation(10, fix = 7)

10×10 SparseArrays.SparseMatrixCSC{Int8, Int64} with 10 stored entries: 
 1  ⋅  ⋅  ⋅  ⋅  ⋅  ⋅  ⋅  ⋅  ⋅
 ⋅  1  ⋅  ⋅  ⋅  ⋅  ⋅  ⋅  ⋅  ⋅
 ⋅  ⋅  ⋅  ⋅  ⋅  ⋅  ⋅  ⋅  1  ⋅
 ⋅  ⋅  ⋅  1  ⋅  ⋅  ⋅  ⋅  ⋅  ⋅
 ⋮              ⋮
 ⋅  ⋅  ⋅  ⋅  ⋅  ⋅  1  ⋅  ⋅  ⋅
 ⋅  ⋅  ⋅  ⋅  ⋅  ⋅  ⋅  1  ⋅  ⋅
 ⋅  ⋅  1  ⋅  ⋅  ⋅  ⋅  ⋅  ⋅  ⋅
 ⋅  ⋅  ⋅  ⋅  ⋅  ⋅  ⋅  ⋅  ⋅  1

```
