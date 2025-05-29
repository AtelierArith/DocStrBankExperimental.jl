```julia
printstatus(r::GitOut.Repo; ...)
printstatus(r::GitOut.Repo, pathspec; kw...)

```

コマンドライン `git status` によって返されるように、ステータスを `stdout` に出力します。追加の引数は [`rawstatus`](@ref) に渡されます。
