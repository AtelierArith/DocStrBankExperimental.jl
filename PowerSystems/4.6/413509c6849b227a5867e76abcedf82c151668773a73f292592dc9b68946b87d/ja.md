```julia
System(
    file_path::AbstractString;
    assign_new_uuids,
    try_reimport,
    kwargs...
) -> Any

```

ファイルパスが .m、.raw、または .json で終わる System を構築します。

ファイルが JSON の場合、`assign_new_uuids = true` はシステムとすべてのコンポーネントの新しい UUID を生成します。ファイルが .raw の場合、`try_reimport = false` は同じディレクトリ内で `<name>_export_metadata.json` ファイルを検索するのをスキップします。
