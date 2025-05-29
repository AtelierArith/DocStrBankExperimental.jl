```julia
seed_gradient(j::Int64, x::Val{N}) -> Any

```

`x::SVector{N,Float64}`オブジェクトを作成します。これは`x[j]`で1になり、他のすべての場所では0になります。
