```julia
mutable struct DMDSVD{T} <: DataDrivenDMD.AbstractKoopmanAlgorithm
```

コプマン演算子 `K` を `X` の特異値分解に基づいて近似します。次のように表されます：

```julia
K = Y*V*Σ*U'
```

ここで `Y` と `X = U*Σ*V'` はデータ行列です。特異値分解は `truncation` パラメータを介して切り捨てられます。このパラメータは、インデックスベースの切り捨てを示す `Int` または許容誤差ベースの切り捨てを示す `Real` であることができます。演算子の `Eigen` 因子分解を返します。

# フィールド

  * `truncation`: 切り捨てを示します

# シグネチャ
