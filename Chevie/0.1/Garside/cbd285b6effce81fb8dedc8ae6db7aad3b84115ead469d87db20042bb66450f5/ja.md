`Brieskorn_normal_form(b::LocallyGarsideElt)`

Brieskorn citeBri71 は、`L(b)` が `b` の左降下集合であり（[`leftdescents`](@ref) を参照）、`b_(L(b))` が `L(b)` の右最小公倍数である場合、`b_(L(b))` が `b` を左で割ることに気づきました。これにより、`b` を `b_(L(b))` で割り、商に対してこのプロセスを続けることができます。このようにして、`b=b_(L₁)⋯ b_(Lᵣ)` という表現を得ることができ、ここで `Lᵢ=L(b_(Lᵢ)⋯ b_(Lᵣ))` がすべての `i` に対して成り立ちます。これを `b` の *Brieskorn 正規形* と呼びます。関数 `Brieskorn_normal_form` は、この形の説明を返し、上記の分解を説明する `L(b)` の集合のリストを返します。

```julia-repl
julia> W=coxgroup(:E,8);B=BraidMonoid(W)
BraidMonoid(E₈)

julia> w=B(2,3,4,2,3,4,5,4,2,3,4,5,6,5,4,2,3,4,5,6,7,6,5,4,2,3,4,5,6,7,8)
2342345423456542345676542345678

julia> Brieskorn_normal_form(w)
2-element Vector{Vector{Int64}}:
 [2, 3, 4, 5, 6, 7]
 [8]

julia> Brieskorn_normal_form(w^2)
2-element Vector{Vector{Int64}}:
 [2, 3, 4, 5, 6, 7, 8]
 [2, 3, 4, 5, 6]
```
