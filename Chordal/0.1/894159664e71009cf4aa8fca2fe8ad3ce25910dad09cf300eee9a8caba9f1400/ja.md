```
edm_completion(A::SparseMatrixCSC{Tv, Ti}) where {Tv <: AbstractFloat, Ti <: Integer}
```

`A`がEDM-completableである場合、[VA15]のアルゴリズム11.1を使用してユークリッド距離行列の補完を返します。

# 参考文献

[VA15] [Chordal Graphs and Semidefinite Optimization](https://www.seas.ucla.edu/~vandenbe/publications/chordalsdp.pdf) by Lieven Vandenberghe and Martin Andersen
