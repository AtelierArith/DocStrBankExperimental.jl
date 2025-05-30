```
cached_download(
    hgfurl :: HuggingFaceURL;
    local_files_only :: Bool = false,
    auth_token :: Union{AbstractString, Nothing} = nothing,
)
```

指定されたURLのローカルキャッシュを見つけるか、ダウンロードを行います。`local_files_only`が設定されている場合、キャッシュからファイルを見つけようとし、見つからない場合はエラーになります。プライベートリポジトリからダウンロードするには、`auth_token`を設定する必要があり、事前に`HuggingFaceApi.login()`を実行する必要があります。

参照: [`HuggingFaceURL`](@ref), [`login`](@ref)
