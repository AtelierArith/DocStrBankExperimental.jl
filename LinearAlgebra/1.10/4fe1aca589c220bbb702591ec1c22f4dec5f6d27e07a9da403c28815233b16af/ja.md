```
istriu(A::AbstractMatrix, k::Integer = 0) -> Bool
```

`A`が`k`番目のスーパー対角線から始まる上三角行列であるかどうかをテストします。

# 例

```jldoctest
julia> a = [1 2; 2 -1]
2×2 Matrix{Int64}:
 1   2
 2  -1

julia> istriu(a)
false

julia> istriu(a, -1)
true

julia> b = [1 im; 0 -1]
2×2 Matrix{Complex{Int64}}:
 1+0im   0+1im
 0+0im  -1+0im

julia> istriu(b)
true

julia> istriu(b, 1)
false
```
