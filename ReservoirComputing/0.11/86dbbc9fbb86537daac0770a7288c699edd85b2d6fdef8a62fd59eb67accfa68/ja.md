```
StandardStates()
```

この構造体が使用されると、貯水池の状態は変更されません。

# 例

```jldoctest
julia> states = StandardStates()
StandardStates()

julia> test_vec = zeros(Float32, 5)
5-element Vector{Float32}:
 0.0
 0.0
 0.0
 0.0
 0.0

julia> new_vec = states(test_vec)
5-element Vector{Float32}:
 0.0
 0.0
 0.0
 0.0
 0.0

julia> test_mat = zeros(Float32, 5, 5)
5×5 Matrix{Float32}:
 0.0  0.0  0.0  0.0  0.0
 0.0  0.0  0.0  0.0  0.0
 0.0  0.0  0.0  0.0  0.0
 0.0  0.0  0.0  0.0  0.0
 0.0  0.0  0.0  0.0  0.0

julia> new_mat = states(test_mat)
5×5 Matrix{Float32}:
 0.0  0.0  0.0  0.0  0.0
 0.0  0.0  0.0  0.0  0.0
 0.0  0.0  0.0  0.0  0.0
 0.0  0.0  0.0  0.0  0.0
 0.0  0.0  0.0  0.0  0.0
```
