```
copy_axis(;
    destination::DafWriter,
    source::DafReader,
    axis::AbstractString,
    [rename::Maybe{AbstractString} = nothing,
    default::Union{Nothing, UndefInitializer} = undef]
)::Nothing
```

ある `source` [`DafReader`](@ref) から別の `destination` [`DafWriter`](@ref) に `axis` をコピーします。

`axis` は `name` と `default` を使用して取得されます。`rename` が指定されている場合は、この名前を使用して `axis` を保存します。
