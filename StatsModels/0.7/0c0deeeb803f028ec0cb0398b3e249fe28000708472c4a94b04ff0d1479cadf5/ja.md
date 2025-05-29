```
MatrixTerm{Ts} <: AbstractTerm
```

単一の数値行列を生成するために組み合わされるべき項のコレクションです。

行列項は、[`collect_matrix_terms`](@ref)を使用して項のタプルから[`apply_schema`](@ref)によって作成され、これは、デフォルトですべての`AbstractTerm`に対して真である特性関数[`is_matrix_term`](@ref)によって行列項として判断されるすべての項を引き出します。
