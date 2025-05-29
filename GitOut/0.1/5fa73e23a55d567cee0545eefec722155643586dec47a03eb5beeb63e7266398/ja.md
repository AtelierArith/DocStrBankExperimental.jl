```julia
rungit(r::GitOut.Repo; ...) -> SubString{String}
rungit(r::GitOut.Repo, args; kw...) -> Any

```

リポジトリ `r` に対して git コマンドを実行します。追加のキーワード引数は [`rungit`](@ref) に渡されます。
