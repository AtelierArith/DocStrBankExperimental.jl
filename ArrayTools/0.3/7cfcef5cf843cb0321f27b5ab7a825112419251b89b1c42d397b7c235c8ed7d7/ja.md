```
is_fast_array(A)
```

は、配列 `A` が標準の1ベースのインデックスを持ち、線形インデックスによって効率的にインデックス付けされているかどうかを返します。

複数の引数を1回の呼び出しでチェックすることができます：

```
is_fast_array(A, B, C, ...)
```

は次のように同じです：

```
is_fast_array(A) && is_fast_array(B) && is_fast_array(C) && ...
```

さらに [`IndexingType`](@ref)、[`to_fast_array`](@ref)、[`is_flat_array`](@ref) を参照してください。
