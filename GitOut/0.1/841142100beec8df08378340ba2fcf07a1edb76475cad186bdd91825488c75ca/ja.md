```julia
push(r::GitOut.Repo; ...) -> GitOut.Repo
push(
    r::GitOut.Repo,
    rem::AbstractString;
    branch,
    delete,
    tags,
    kw...
) -> GitOut.Repo

```

リポジトリ `r` の更新でリモートを更新します。追加のキーワード引数は [`rungit`](@ref) に渡されます。
