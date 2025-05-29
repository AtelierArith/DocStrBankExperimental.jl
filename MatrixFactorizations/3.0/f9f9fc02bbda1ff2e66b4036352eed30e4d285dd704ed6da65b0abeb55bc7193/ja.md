```
ul!(A, pivot=Val(true); check = true) -> UL
```

`ul!` は [`ul`](@ref) と同じですが、入力 `A` を上書きすることでスペースを節約します。因子分解が `A` の要素型で表現できない数を生成した場合、例えば整数型の場合、[`InexactError`](@ref) 例外がスローされます。

# 例

```jldoctest
julia> A = [4. 3.; 6. 3.]
2×2 Array{Float64,2}:
 4.0  3.0
 6.0  3.0

julia> F = ul!(A)
UL{Float64,Array{Float64,2},Vector{Int}}
L 因子:
2×2 Array{Float64,2}:
 1.0       0.0
 0.666667  1.0
U 因子:
2×2 Array{Float64,2}:
 6.0  3.0
 0.0  1.0

julia> iA = [4 3; 6 3]
2×2 Array{Int64,2}:
 4  3
 6  3

julia> ul!(iA)
ERROR: InexactError: Int64(0.6666666666666666)
Stacktrace:
[...]
```
