```
get_private_fields(::Type{T}) where {T}
```

型 `T` のプライベートフィールドを返します。これは [`@private_struct`](@ref) によって示されます。

デフォルトは `()` です。
