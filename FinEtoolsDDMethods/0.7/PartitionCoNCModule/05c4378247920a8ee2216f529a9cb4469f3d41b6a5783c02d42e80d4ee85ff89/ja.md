```
CoNCPartitionData(cpi::CPI, 
rank, 
fes, 
make_matrix, 
make_interior_load = nothing
) where {CPI<:CoNCPartitioningInfo}
```

パーティションデータを作成します。

# 引数

  * `cpi`: パーティショニング情報
  * `rank`: パーティションのランク、ゼロベース
  * `fes`: 有限要素セット
  * `make_matrix`: 特定の有限要素サブセットのための行列を作成する関数
  * `make_interior_load`: 特定の有限要素サブセットのための内部荷重ベクトルを作成する関数
