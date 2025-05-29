```julia
addremote(
    r::GitOut.Repo,
    name::AbstractString,
    url::AbstractString;
    fetch,
    tags,
    no_tags,
    kw...
) -> GitOut.Repo

```

リポジトリに `name` という名前のリモートを追加し、URL `url` を指します。追加のキーワード引数は [`rungit`](@ref) に渡されます。
