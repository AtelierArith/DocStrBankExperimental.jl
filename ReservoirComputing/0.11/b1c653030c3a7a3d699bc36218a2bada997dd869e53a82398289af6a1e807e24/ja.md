```
PaddedStates(padding)
PaddedStates(;padding=1.0)
```

指定されたパディング値（デフォルトは1.0）で `PaddedStates` 構造体のインスタンスを作成します。リザーバーの状態は、パディング値を垂直に連結することでパディングされます。

# 例

```jldoctest
julia> states = PaddedStates(1.0)
PaddedStates{Float64}(1.0)

julia> test_vec = zeros(Float32, 5)
5-element Vector{Float32}:
 0.0
 0.0
 0.0
 0.0
 0.0

julia> new_vec = states(test_vec)
6-element Vector{Float32}:
 0.0
 0.0
 0.0
 0.0
 0.0
 1.0

julia> test_mat = zeros(Float32, 5, 5)
5×5 Matrix{Float32}:
 0.0  0.0  0.0  0.0  0.0
 0.0  0.0  0.0  0.0  0.0
 0.0  0.0  0.0  0.0  0.0
 0.0  0.0  0.0  0.0  0.0
 0.0  0.0  0.0  0.0  0.0

julia> new_mat = states(test_mat)
6×5 Matrix{Float32}:
 0.0  0.0  0.0  0.0  0.0
 0.0  0.0  0.0  0.0  0.0
 0.0  0.0  0.0  0.0  0.0
 0.0  0.0  0.0  0.0  0.0
 0.0  0.0  0.0  0.0  0.0
 1.0  1.0  1.0  1.0  1.0
```
