```
h5open(file_image::Vector{UInt8}, mode::AbstractString="r";
    name=nothing,
    fapl=FileAccessProperties(),
    increment=8192,
    backing_store=false,
    write_tracking=false,
    page_size=524288,
    pv...
)
```

`Vector{UInt8}`に含まれるファイルイメージを開きます。 [`API.h5p_set_file_image`](@ref)を参照してください。

[`Drivers.Core`](@ref)とは異なり、ここでのデフォルトはバックストアを使用しないことです。
