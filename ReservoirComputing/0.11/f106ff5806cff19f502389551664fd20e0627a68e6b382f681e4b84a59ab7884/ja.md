```
ExtendedStates()
```

`ExtendedStates` 構造体は、入力データ（トレーニング中）と予測データ（予測フェーズ中）を縦に連結することによって、貯水池の状態を拡張するために使用されます。

# 例

```jldoctest
julia> states = ExtendedStates()
ExtendedStates()

julia> test_vec = zeros(Float32, 5)
5-element Vector{Float32}:
 0.0
 0.0
 0.0
 0.0
 0.0

julia> new_vec = states(test_vec, fill(3.0f0, 3))
8-element Vector{Float32}:
 0.0
 0.0
 0.0
 0.0
 0.0
 3.0
 3.0
 3.0

julia> test_mat = zeros(Float32, 5, 5)
5×5 Matrix{Float32}:
 0.0  0.0  0.0  0.0  0.0
 0.0  0.0  0.0  0.0  0.0
 0.0  0.0  0.0  0.0  0.0
 0.0  0.0  0.0  0.0  0.0
 0.0  0.0  0.0  0.0  0.0

julia> new_mat = states(test_mat, fill(3.0f0, 3))
8×5 Matrix{Float32}:
 0.0  0.0  0.0  0.0  0.0
 0.0  0.0  0.0  0.0  0.0
 0.0  0.0  0.0  0.0  0.0
 0.0  0.0  0.0  0.0  0.0
 0.0  0.0  0.0  0.0  0.0
 3.0  3.0  3.0  3.0  3.0
 3.0  3.0  3.0  3.0  3.0
 3.0  3.0  3.0  3.0  3.0
```
