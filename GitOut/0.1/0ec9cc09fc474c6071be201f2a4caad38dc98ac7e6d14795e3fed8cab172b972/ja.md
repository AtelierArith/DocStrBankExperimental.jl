```julia
pull(r::GitOut.Repo; ...) -> GitOut.Repo
pull(
    r::GitOut.Repo,
    rem::AbstractString;
    branch,
    rebase,
    depth,
    prune,
    tags,
    jobs,
    kw...
) -> GitOut.Repo

```

リモート名 `rem` からリポジトリ `r` への更新を取得します。追加のキーワード引数は [`rungit`](@ref) に渡されます。
