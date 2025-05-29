```julia
git(r::GitOut.Repo; ...) -> Cmd
git(r::GitOut.Repo, args; kw...) -> Cmd

```

リポジトリ `r` のために git コマンドを実行する `Cmd` オブジェクトを作成します。追加のキーワード引数は [`git`](@ref) に渡されます。
