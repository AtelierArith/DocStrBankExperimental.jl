```
derivative!(
    res,
    f::Function,
    m::Integer,
    n::Integer,
    x::Union{Cdouble,Vector{Cdouble}},
    mode::Symbol;
    dir::Union{Vector{Cdouble},Matrix{Cdouble}}=Vector{Cdouble}(),
    weights::Union{Vector{Cdouble},Matrix{Cdouble}}=Vector{Cdouble}(),
    tape_id::Integer=0,
    reuse_tape::Bool=false,
)
```

[`derivative`](@ref) ドライバーのバリアントで、[一次](@ref "First-Order")、[二次](@ref "Second-Order")、および [絶対正規形](@ref "Abs-Normal-Form") の計算を行い、ユーザーが結果 `res` のために事前に割り当てられたコンテナを提供できるようにします。コンテナは、[`allocator`](@ref) または [`init_abs_normal_form`](@ref) メソッドを利用して割り当てることができます。[`derivative`](@ref) の引数に加えて、関数 `f` の出力次元 `m` と入力次元 `n` が必要です。選択した点 `x` で関数 `f` の有効なテープがすでにある場合は、`reuse_tape=true` を使用し、テープの再作成を避けるために `tape_id` を適切に設定します。

例:

```jldoctest
f(x) = [cos(x[1]), x[2]*x[3]]
x = [0.0, 1.5, -1.0]
mode = :hess_mat
dir = [[1.0, -1.0, 1.0] [0.5, -0.5, 1.0]]
m = 2
n = 3
res =  allocator(m, n, mode, size(dir, 2)[1], 0)
derivative!(res, f, m, n, x, mode, dir=dir)
res
# output

2×3×2 CxxTensor:
[:, :, 1] =
 -1.0  0.0   0.0
  0.0  1.0  -1.0

[:, :, 2] =
 -0.5  0.0   0.0
  0.0  1.0  -0.5
```

```jldoctest
f(x) = max(x[1]*x[2], x[1]^2)
x = [1.0, 1.0]
m = 1
n = 2
abs_normal_form = init_abs_normal_form(f, x)
derivative!(abs_normal_form, f, m, n, x, :abs_normal, tape_id=abs_normal_form.tape_id, reuse_tape=true)
abs_normal_form
# output

AbsNormalForm(0, 1, 2, 1, [1.0, 1.0], [1.0], [0.0], [0.0], [1.0], [1.5 0.5], [0.5;;], [1.0 -1.0], [0.0;;])
```
