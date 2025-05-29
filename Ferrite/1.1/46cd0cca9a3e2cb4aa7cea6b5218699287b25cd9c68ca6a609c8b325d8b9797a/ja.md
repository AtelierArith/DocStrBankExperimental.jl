```
finish_assemble(a::COOAssembler) -> K, f
```

アセンブリを完了し、スパース行列 `K::SparseMatrixCSC` とベクトル `f::Vector` を返します。アセンブラがベクトルアセンブリに使用されていない場合、`f` は空のベクトルです。
