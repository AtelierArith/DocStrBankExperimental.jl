```
hf_hub_download(
    repo_id :: AbstractString,
    filename :: AbstractString;
    repo_type = nothing,
    revision = "main",
    auth_token :: Union{AbstractString, Nothing} = get_token(),
    local_files_only :: Bool  = false,
    cache :: Bool = true,
)
```

[`HuggingFaceURL`](@ref)を構築し、[`cached_download`](@ref)を実行します。`cache`が`false`の場合、`tempname()`によって生成された名前で一時ディレクトリにファイルをダウンロードします。`local_files_only`が設定されている場合、`cache`も設定されている必要があります。
