```
istril(A::AbstractMatrix, k::Integer = 0) -> Bool
```

`A` が `k` 番目のスーパー対角線から始まる下三角行列であるかどうかをテストします。

# 例

```jldoctest
julia> a = [1 2; 2 -1]
2×2 Matrix{Int64}:
 1   2
 2  -1

julia> istril(a)
false

julia> istril(a, 1)
true

julia> b = [1 0; -im -1]
2×2 Matrix{Complex{Int64}}:
 1+0im   0+0im
 0-1im  -1+0im

julia> istril(b)
true

julia> istril(b, -1)
false
```
