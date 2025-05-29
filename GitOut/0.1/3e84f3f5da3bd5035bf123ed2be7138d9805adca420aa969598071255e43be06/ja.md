```julia
printstatus(io::IO, r::GitOut.Repo; ...)
printstatus(io::IO, r::GitOut.Repo, pathspec; kw...)

```

コマンドライン `git status` によって返されるようにステータスを表示します。追加の引数は [`rawstatus`](@ref) に渡されます。
