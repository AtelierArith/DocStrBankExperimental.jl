```
neg(vector) -> vector
```

新しいベクトルを返し、`vector`内のすべてのNaNおよび正の値をゼロにします。Matlabのmin(0, vector)を模倣します。`vector`がスカラーの場合はスカラーを返します。

# 例

```jldoctest
julia> vector = [1, 2, 3, NaN, -1 ]

julia> neg(vector)
5-element Vector{Float64}:
0.0
0.0
0.0
0.0
-1.0
```
