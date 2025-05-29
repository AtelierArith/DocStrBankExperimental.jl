```
pos(vector) -> vector
```

新しいベクトルを返します。`vector`内のすべてのNaNおよび負の値をゼロに置き換えます。Matlabのmax(0, vector)を模倣します。`vector`がスカラーの場合はスカラーを返します。

# 例

```jldoctest
julia> vector = [1, 2, 3, NaN, -1 ]

julia> pos(vector)
5-element Vector{Float64}:
 1.0
 2.0
 3.0
 0.0
 0.0
```
