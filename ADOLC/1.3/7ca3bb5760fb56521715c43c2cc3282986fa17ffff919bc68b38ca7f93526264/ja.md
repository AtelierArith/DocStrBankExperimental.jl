```
derivative(
    f::Function,
    x::Union{Cdouble,Vector{Cdouble}},
    partials::Vector{Vector{Int64}};
    tape_id::Integer=0,
    reuse_tape::Bool=false,
    id_seed::Bool=false,
    adolc_format::Bool=false,
)
```

[`derivative`](@ref) ドライバーのバリアントで、点 `x` での関数 `f` の [高次](@ref "Higher-Order") 導関数を計算するために使用できます。導関数は `partials` ベクター内の混合偏導関数として指定されます。偏導関数を定義するには、[Partial-Format](@ref) または [ADOLC-Format](@ref) を使用し、`adolc_format` を適切に設定します。フラグ `id_seed` は、[シード行列生成](@ref "Seed-Matrix") の方法を指定するために使用されます。基盤となる方法は、識別子 `tape_id` を持つテープを利用します。選択した点 `x` で関数 `f` に対してすでに有効なテープがある場合は、`reuse_tape=true` を使用し、テープの再作成を避けるために `tape_id` を適切に設定します。

# 例:

Partial-Format:

```jldoctest
f(x) = [x[1]^2*x[2]^2, x[3]^2*x[4]^2]
x = [1.0, 2.0, 3.0, 4.0]
partials = [[1, 1, 0, 0], [0, 0, 1, 1], [2, 2, 0, 0]]
res = derivative(f, x, partials)

# 出力

2×3 CxxMatrix:
 8.0   0.0  4.0
 0.0  48.0  0.0
```

ADOLC-Format:

```jldoctest
f(x) = [x[1]^2*x[2]^2, x[3]^2*x[4]^2]
x = [1.0, 2.0, 3.0, 4.0]
partials = [[2, 1, 0, 0], [4, 3, 0, 0], [2, 2, 1, 1]]
res = derivative(f, x, partials, adolc_format=true)

# 出力

2×3 CxxMatrix:
 8.0   0.0  4.0
 0.0  48.0  0.0
```
