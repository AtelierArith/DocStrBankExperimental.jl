```
  parent_type(W::Type{<:WrappedArray})
```

ラップされた配列型の親タイプを返します。これは、ラッパーによってラップされた配列の型です。例えば、`parent_type(SubArray{Int, 1, Matrix{Int}}) == Matrix{Int}` です。
