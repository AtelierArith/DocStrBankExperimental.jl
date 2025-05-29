```julia
add(
    r::GitOut.Repo,
    pathspec::AbstractVector;
    force,
    interactive,
    edit,
    all,
    kw...
) -> GitOut.Repo

```

リポジトリ `r` のインデックスにファイルの内容を追加します。追加のキーワード引数は [`rungit`](@ref) に渡されます。
