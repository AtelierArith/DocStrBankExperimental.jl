```
derivative!(
    res,
    f,
    m::Integer,
    n::Integer,
    x::Union{Cdouble,Vector{Cdouble}},
    partials::Vector{Vector{Int64}},
    seed::CxxMatrix;
    tape_id::Integer=0,
    reuse_tape::Bool=false,
    adolc_format::Bool=false,
)
```

[`derivative!`](@ref) ドライバーのバリアントで、[高次](@ref "Higher-Order") 導関数の計算に `seed` が必要です。`seed` の背後にあるアイデアの詳細は [こちら](@ref "Seed-Matrix") で確認できます。

例:

```jldoctest
f(x) = [x[1]^4, x[2]^3*x[1]]
x = [1.0, 2.0]
partials = [[1], [2], [3]]
seed = CxxMatrix([[1.0, 1.0];;])
m = 2
n = 2
res = CxxMatrix(m, length(partials))
derivative!(res, f, m, n, x, partials, seed)
res

# output

2×3 CxxMatrix:
  4.0  12.0  24.0
 20.0  36.0  42.0
```
