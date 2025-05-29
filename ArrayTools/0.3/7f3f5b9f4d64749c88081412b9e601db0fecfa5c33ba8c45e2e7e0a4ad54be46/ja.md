```
is_flat_array(A) -> boolean
```

は、配列 `A` が *フラット* 配列としてインデックス付けできるかどうかを示します。つまり、列優先順序で連続した要素を持ち、最初の要素がインデックス 1 にある配列です。これはまた、`A` がすべての次元で 1 ベースのインデックスを持つことを意味します。

複数の引数を単一の呼び出しでチェックすることができます：

```
is_flat_array(A, B, C, ...)
```

は次のように同じです：

```
is_flat_array(A) && is_flat_array(B) && is_flat_array(C) && ...
```

詳細については、[`StorageType`](@ref)、[`to_flat_array`](@ref)、[`is_fast_array`](@ref)、[`has_standard_indexing`](@ref) を参照してください。
