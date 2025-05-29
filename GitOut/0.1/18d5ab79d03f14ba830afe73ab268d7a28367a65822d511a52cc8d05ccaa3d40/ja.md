```julia
clone(
    url::URIs.URI,
    path::AbstractString;
    kw...
) -> GitOut.Repo

```

リモートの `url` からパス `path` に git リポジトリをクローンします。追加のキーワード引数は [`rungit`](@ref) に渡されます。
