```
cell(arr::Array, args...;kwargs...)
```

セルテンソルを構築します。

# 例

```julia-REPL
julia> r = cell([[1.],[2.,3.]])
julia> run(sess, r[1])
1-element Array{Float32,1}:
 1.0
julia> run(sess, r[2])
2-element Array{Float32,1}:
 2.0
 3.0
```
