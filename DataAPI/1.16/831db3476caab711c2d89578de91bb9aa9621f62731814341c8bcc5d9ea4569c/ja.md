```
metadatasupport(T::Type)
```

型 `T` の値がメタデータをサポートしているかどうかを示す `NamedTuple{(:read, :write), Tuple{Bool, Bool}}` を返します。

`read` フィールドは、[`metadata`](@ref) および [`metadatakeys`](@ref) 関数を使用してメタデータを読み取ることがサポートされているかどうかを示します。

`write` フィールドは、[`metadata!`](@ref)、[`deletemetadata!`](@ref)、および [`emptymetadata!`](@ref) 関数を使用してメタデータを変更することがサポートされているかどうかを示します。
