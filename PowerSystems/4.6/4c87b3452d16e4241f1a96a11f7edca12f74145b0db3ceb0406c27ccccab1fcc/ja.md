```julia
System(
    file_path::AbstractString,
    md::Dict;
    kwargs...
) -> Any

```

`.raw`ファイルと`<name>_export_metadata.json`ファイルに対応する辞書からSystemを構築します。
