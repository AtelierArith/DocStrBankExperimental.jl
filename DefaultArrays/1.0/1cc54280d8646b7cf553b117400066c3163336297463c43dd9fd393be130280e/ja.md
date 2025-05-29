DefaultArray(default, size...)

DefaultArrayを作成します

例 1:

```julia
julia> DefaultArray("X",3,3)
3×3 DefaultArray{String,2}:
 "X"  "X"  "X"
 "X"  "X"  "X"
 "X"  "X"  "X"
```

例 2:

```julia
julia> DefaultArray(false,3,4)
3×4 DefaultArray{Bool,2}:
 0  0  0  0
 0  0  0  0
 0  0  0  0
```

DefaultArray(default, A::AbstractArray)

例 3:

```julia
DefaultArray(false,rand(Bool,5,5))
5×5 DefaultArray{Bool,2}:
1  0  0  1  0
1  1  1  1  1
1  1  1  0  0
0  1  0  0  1
0  0  1  1  0
```
