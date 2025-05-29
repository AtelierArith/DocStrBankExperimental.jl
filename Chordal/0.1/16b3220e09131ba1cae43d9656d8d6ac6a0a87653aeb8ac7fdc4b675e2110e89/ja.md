```
maxdet_completion(A::SparseMatrixCSC{Tv, Ti}) where {Tv <: AbstractFloat, Ti <: Integer}
```

弦状スパース行列 `A` の最大行列式補完を、[VA15] のアルゴリズム 10.2 を使用して返します。

# 参考文献

[VA15] [Chordal Graphs and Semidefinite Optimization](https://www.seas.ucla.edu/~vandenbe/publications/chordalsdp.pdf) by Lieven Vandenberghe and Martin Andersen
