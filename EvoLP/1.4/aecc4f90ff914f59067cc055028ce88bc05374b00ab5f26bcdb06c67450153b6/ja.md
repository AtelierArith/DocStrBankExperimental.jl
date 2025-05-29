```
binary_vector_pop(n, l; rng=Random.GLOBAL_RNG)
```

`n` 個のベクトルバイナリ個体を生成し、それぞれの長さは `l` です。

# 例

```julia
julia> using EvoLP

julia> binary_vector_pop(2, 5)
2-element Vector{BitVector}:
 [1, 0, 1, 1, 0]
 [0, 1, 0, 0, 0]
```
