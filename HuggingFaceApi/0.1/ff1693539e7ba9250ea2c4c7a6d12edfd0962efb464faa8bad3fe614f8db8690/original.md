```
cached_download(
    hgfurl :: HuggingFaceURL;
    local_files_only :: Bool = false,
    auth_token :: Union{AbstractString, Nothing} = nothing,
)
```

Find the local cache of given url or do downloading. If `local_files_only` is set, it will try to  find the file from cache, and error out when not found. For downloading from private repo,  `auth_token` need to be set, or do `HuggingFaceApi.login()` beforehand.

See also: [`HuggingFaceURL`](@ref), [`login`](@ref)
