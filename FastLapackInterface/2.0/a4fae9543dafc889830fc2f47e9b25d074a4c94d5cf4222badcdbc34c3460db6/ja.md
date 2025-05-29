```
LSEWs
```

最小二乗解法関数 [`LAPACK.geqrf!`](@ref) のワークスペース。

# 例

```jldoctest
julia> A = [1.2 2.3 6.2
            6.2 3.3 8.8
            9.1 2.1 5.5]
3×3 Matrix{Float64}:
 1.2  2.3  6.2
 6.2  3.3  8.8
 9.1  2.1  5.5

julia> B = [2.7 3.1 7.7
            4.1 8.1 1.8]
2×3 Matrix{Float64}:
 2.7  3.1  7.7
 4.1  8.1  1.8

julia> c = [0.2, 7.2, 2.9]
3-element Vector{Float64}:
 0.2
 7.2
 2.9

julia> d = [3.9, 2.1]
2-element Vector{Float64}:
 3.9
 2.1

julia> ws = LSEWs(A, B)
LSEWs{Float64}
  work: 101-element Vector{Float64}
  X: 3-element Vector{Float64}

julia> LAPACK.gglse!(ws, A, c, B, d)
([0.19723156207005318, 0.0683561362406917, 0.40981438442398854], 13.750943845251626)
```
