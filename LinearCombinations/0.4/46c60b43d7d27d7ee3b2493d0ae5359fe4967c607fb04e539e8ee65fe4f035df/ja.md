```
TensorSlurp(f)
```

`TensorSlurp`は、`Tensor`項に作用する線形関数を多重線形関数に変換します。これは、Juliaにおける[スラープ](https://docs.julialang.org/en/v1/manual/faq/#...-combines-many-arguments-into-one-argument-in-function-definitions)に似ています。

新しい関数は常に線形結合を返します。引数のいずれかが線形結合でなくてもです。これは、`@linear`で議論されたすべてのキーワード引数を認識します。未知のキーワード引数は`f`に渡されます。

他に[`Tensor`](@ref)、[`tensor`](@ref)、[`TensorSplat`](@ref)、[`@linear`](@ref)も参照してください。

# 例

[`swap`](@ref)をテンソルに作用する関数の例として使用します。

```jldoctest
julia> const f = TensorSlurp(swap)
TensorSlurp(Regroup{(1, 2),(2, 1)})

julia> a = Linear('x' => 1, 'y' => 2)
Linear{Char, Int64} with 2 terms:
'x'+2*'y'

julia> b = Linear("w" => 3, "z" => -1)
Linear{String, Int64} with 2 terms:
3*"w"-"z"

julia> c = tensor(a, b)
Linear{Tensor{Tuple{Char, String}}, Int64} with 4 terms:
3*'x'⊗"w"-'x'⊗"z"-2*'y'⊗"z"+6*'y'⊗"w"

julia> swap(c)
Linear{Tensor{Tuple{String, Char}}, Int64} with 4 terms:
-"z"⊗'x'-2*"z"⊗'y'+6*"w"⊗'y'+3*"w"⊗'x'

julia> f(a, b)
Linear{Tensor{Tuple{String, Char}}, Int64} with 4 terms:
-"z"⊗'x'-2*"z"⊗'y'+6*"w"⊗'y'+3*"w"⊗'x'

julia> f(a, b; addto = swap(c), coeff = -1)
Linear{Tensor{Tuple{String, Char}}, Int64} with 0 terms:
0
```
