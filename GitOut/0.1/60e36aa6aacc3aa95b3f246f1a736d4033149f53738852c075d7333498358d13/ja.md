```julia
getremoteurl(
    r::GitOut.Repo,
    name::AbstractString;
    kw...
) -> Any

```

リポジトリ `r` の `name` という名前のリモートのURLを取得します。追加のキーワード引数は [`rungit`](@ref) に渡されます。
