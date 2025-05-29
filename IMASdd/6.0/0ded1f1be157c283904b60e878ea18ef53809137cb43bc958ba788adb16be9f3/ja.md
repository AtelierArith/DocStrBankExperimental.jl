```
h5merge(
    output_file::AbstractString,
    directory::AbstractString;
    mode::AbstractString="a",
    skip_existing_entries::Bool=false,
    follow_symlinks::Bool=false,
    verbose::Bool=false,
    include_base_dir::Bool=false,
    pattern::Union{Regex,Nothing}=nothing,
    kwargs...
    )
```

ディレクトリ（およびサブディレクトリ）のすべてのファイルをHDF5 `output_file` に追加します。
