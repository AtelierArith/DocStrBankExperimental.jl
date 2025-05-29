```
colmetadatasupport(T::Type)
```

型 `T` の値が列メタデータをサポートしているかどうかを示す `NamedTuple{(:read, :write), Tuple{Bool, Bool}}` を返します。

`read` フィールドは、[`colmetadata`](@ref) および [`colmetadatakeys`](@ref) 関数を使用してメタデータを読み取ることがサポートされているかどうかを示します。

`write` フィールドは、[`colmetadata!`](@ref)、[`deletecolmetadata!`](@ref)、および [`emptycolmetadata!`](@ref) 関数を使用してメタデータを変更することがサポートされているかどうかを示します。
