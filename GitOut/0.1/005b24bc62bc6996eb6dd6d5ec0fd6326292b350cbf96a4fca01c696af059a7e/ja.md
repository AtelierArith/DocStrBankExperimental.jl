```julia
remove(r::GitOut.Repo; ...) -> GitOut.Repo
remove(
    r::GitOut.Repo,
    pathspec::AbstractVector{<:AbstractString};
    force,
    recursive,
    kw...
) -> GitOut.Repo

```

リポジトリ `r` の作業ツリーとインデックスからファイルを削除します。追加のキーワード引数は [`rungit`](@ref) に渡されます。
