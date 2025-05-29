```
h5merge(
    output_file::AbstractString,
    directories::AbstractVector{<:AbstractString};
    include_base_dir::Bool=true,
    cleanup::Bool=false,
    kwargs...)
```

複数のディレクトリ（およびそのサブディレクトリ）内のすべてのファイルをHDF5 `output_file` に追加します。
