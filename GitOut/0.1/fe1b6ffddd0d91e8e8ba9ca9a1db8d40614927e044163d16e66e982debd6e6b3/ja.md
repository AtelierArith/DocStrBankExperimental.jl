```julia
commit(r::GitOut.Repo; ...) -> GitOut.Repo
commit(
    r::GitOut.Repo,
    pathspec::AbstractVector{<:AbstractString};
    all,
    author,
    date,
    message,
    kw...
) -> GitOut.Repo

```

リポジトリ `r` に変更を記録します。追加のキーワード引数は [`rungit`](@ref) に渡されます。
