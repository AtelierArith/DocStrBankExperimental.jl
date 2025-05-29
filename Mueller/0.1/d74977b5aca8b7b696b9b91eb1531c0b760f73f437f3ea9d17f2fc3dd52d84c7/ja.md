```
linear_polarizer([T=Float64], θ=0; p=1)
```

θによって与えられる透過軸を持つ線形偏光子で、デフォルトでは水平です。部分的な偏光は`p`キーワード引数で指定でき、強度を`p^2/2`の因子で変更します。

# 例

```jldoctest
julia> M = linear_polarizer()
4×4 StaticArrays.SMatrix{4, 4, Float64, 16} with indices SOneTo(4)×SOneTo(4):
 0.5  0.5  0.0  0.0
 0.5  0.5  0.0  0.0
 0.0  0.0  0.0  0.0
 0.0  0.0  0.0  0.0

julia> S = [1, 0, 0, 0]; # I, Q, U, V

julia> M * S # 水平成分のみが残る (+Q)
4-element StaticArrays.SVector{4, Float64} with indices SOneTo(4):
 0.5
 0.5
 0.0
 0.0
```
