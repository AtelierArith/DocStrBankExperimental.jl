```
TensorSplat(f)
```

`TensorSplat`は、マルチリニア関数`f`を、`Tensor`型の項に作用する線形関数に変換します。これは、Juliaにおける[splatting](https://docs.julialang.org/en/v1/manual/faq/#...-splits-one-argument-into-many-different-arguments-in-function-calls)に似ています。

`Tensor`型の引数で呼び出されると、新しい関数はテンソルの成分に対する`f`の値を返します（これは線形結合である場合もあれば、そうでない場合もあります）。この場合、すべてのキーワード引数は`f`に渡されます。

線形結合を引数として呼び出すと、新しい関数は線形結合を返します。これは、`@linear`で議論されたすべてのキーワード引数を認識します。未知のキーワード引数は`f`に渡されます。

他にも[`Tensor`](@ref)、[`tensor`](@ref)、[`TensorSlurp`](@ref)、[`@linear`](@ref)を参照してください。

# 例

```jldoctest
julia> const f = MultilinearExtension(*)
MultilinearExtension(*)

julia> const g = TensorSplat(f)
TensorSplat(MultilinearExtension(*))

julia> a = Linear('x' => 1, 'y' => 2)
Linear{Char, Int64} with 2 terms:
'x'+2*'y'

julia> b = Linear("w" => 3, "z" => -1)
Linear{String, Int64} with 2 terms:
3*"w"-"z"

julia> f(a, b)
Linear{String, Int64} with 4 terms:
3*"xw"-2*"yz"+6*"yw"-"xz"

julia> c = tensor(a, b)
Linear{Tensor{Tuple{Char, String}}, Int64} with 4 terms:
3*'x'⊗"w"-'x'⊗"z"-2*'y'⊗"z"+6*'y'⊗"w"

julia> g(c)
Linear{String, Int64} with 4 terms:
3*"xw"-2*"yz"+6*"yw"-"xz"

julia> g(c; addto = f(a, b), coeff = -1)
Linear{String, Int64} with 0 terms:
0
```
