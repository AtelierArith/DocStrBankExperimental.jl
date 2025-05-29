```
get_sparse_dof_map(trial::FESpace,test::FESpace,args...) -> AbstractDofMap
```

FE問題に関連するヤコビ行列に関するインデックスマップを返します。デフォルトの出力は`TrivialSparseMatrixDofMap`であり、試行空間とテスト空間が`TProductFESpace`型の場合、`SparseMatrixDofMap`が返されます。
