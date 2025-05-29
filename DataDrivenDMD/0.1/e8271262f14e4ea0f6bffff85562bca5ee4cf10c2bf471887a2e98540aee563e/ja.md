```julia
mutable struct DMDPINV <: DataDrivenDMD.AbstractKoopmanAlgorithm
```

コープマン演算子 `K` を次に基づいて近似します。

```julia
K = Y / X
```

ここで `Y` と `X` はデータ行列です。演算子の `Eigen` 因子分解を返します。

# フィールド

# シグネチャ
