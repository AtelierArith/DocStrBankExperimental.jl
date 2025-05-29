```
derivative(
    f::Function,
    x::Union{Cdouble,Vector{Cdouble}},
    mode::Symbol;
    dir::Union{Vector{Cdouble},Matrix{Cdouble}}=Vector{Cdouble}(),
    weights::Union{Vector{Cdouble},Matrix{Cdouble}}=Vector{Cdouble}(),
    tape_id::Integer=0,
    reuse_tape::Bool=false,
)

[`derivative`](@ref) ドライバーのバリアントで、与えられた関数 `f` の点 `x` における [一次](@ref "First-Order") および [二次](@ref "Second-Order") の導関数、ならびに [絶対正規形](@ref "Abs-Normal-Form") を計算するために使用できます。利用可能なモードは [こちら](@ref "Derivative Modes") にリストされています。表の数式は `weights`（左の乗数）と `dir`（右の乗数）を定義します。ほとんどのモードはテープを利用し、その識別子は `tape_id` です。選択した点 `x` において関数 `f` の有効なテープがすでに存在する場合は、`reuse_tape=true` を使用し、テープの再作成を避けるために `tape_id` を適切に設定してください。

# 例:

一次導関数:

```

jldoctest f(x) = sin(x) res = derivative(f, float(π), :jac)

# 出力

1-element CxxVector:  -1.0

```

二次導関数:

```

jldoctest f(x) = [x[1]*x[2]^2, x[1]^2*x[3]^3] x = [1.0, 2.0, -1.0] dir = [1.0, 0.0, 0.0] weights = [1.0, 1.0] res = derivative(f, x, :vec*hess*vec, dir=dir, weights=weights)

# 出力

3-element CxxVector:  -2.0   4.0   6.0

```

絶対正規形:

```

jldoctest f(x) = max(x[1]*x[2], x[1]^2) x = [1.0, 1.0] res = derivative(f, x, :abs_normal)

# 出力

AbsNormalForm(0, 1, 2, 1, [1.0, 1.0], [1.0], [0.0], [0.0], [1.0], [1.5 0.5], [0.5;;], [1.0 -1.0], [0.0;;]) ```
