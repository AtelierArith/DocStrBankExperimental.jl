```
read_solutions(filename)
```

[`write_solutions`](@ref)で保存された解を読み込みます。

## 例

```julia
julia> write_solutions("solutions.txt", [[1, 1], [-1, 2]])

julia> read_solutions("solutions.txt")
2-element Array{Array{Complex{Int64},1},1}:
 [1 + 0im, 1 + 0im]
 [-1 + 0im, 2 + 0im]
```
