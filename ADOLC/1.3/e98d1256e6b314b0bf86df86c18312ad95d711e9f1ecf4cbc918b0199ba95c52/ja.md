```
derivative!(
    res,
    f,
    m::Integer,
    n::Integer,
    x::Union{Cdouble,Vector{Cdouble}},
    partials::Vector{Vector{Int64}};
    tape_id::Integer=0,
    reuse_tape::Bool=false,
    id_seed::Bool=false,
    adolc_format::Bool=false,
)
```

[`derivative`](@ref) ドライバーのバリアントで、[高次](@ref "Higher-Order") 導関数の計算を行い、ユーザーが結果 `res` のために事前に割り当てられたコンテナを提供できるようにします。[`derivative`](@ref) の引数に加えて、関数 `f` の出力次元 `m` と入力次元 `n` が必要です。選択した点 `x` で関数 `f` の有効なテープがすでにある場合は、`reuse_tape=true` を使用し、テープの再作成を避けるために `tape_id` を適切に設定します。

例:

```jldoctest
f(x) = x[1]^4*x[2]*x[3]*x[4]^2
x = [3.0, -1.5, 1.5, -2.0]
partials = [[4, 0, 0, 0], [3, 0, 1, 2]]
m = 1
n = 4
res = CxxMatrix(m, length(partials))
derivative!(res, f, m, n, x, partials)
res

# output

1×2 CxxMatrix:
 -216.0  -216.0
```
