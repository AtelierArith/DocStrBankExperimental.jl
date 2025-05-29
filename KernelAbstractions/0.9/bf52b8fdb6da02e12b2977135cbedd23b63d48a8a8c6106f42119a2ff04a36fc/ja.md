```
get_backend(A::AbstractArray)::Backend
```

配列 `A` に適した [`Backend`](@ref) インスタンスを取得します。

!!! note
    Backend 実装は **必ず** カスタム配列タイプのために `get_backend` を提供しなければなりません。それは [`allocate`](@ref) の戻り値の型と同じであるべきです。

