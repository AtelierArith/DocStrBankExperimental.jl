`generic_order(W,q=Pol())`

は、`W` の一般的な順序を `q` の多項式として返します（Spets の「コンパクト」順序）。これは $q^{Nₕ}Πᵢ(q^{dᵢ}-1)$ であり、ここで `dᵢ` は反射次数、`Nₕ` は反射ハイパープレーンの数です。Weyl群の場合、これは `q` 要素を持つ体上の関連する半単純有限還元群の順序です。

```julia-repl
julia> PermRoot.generic_order(complex_reflection_group(4),Pol(:q))
Pol{Int64}: q¹⁴-q¹⁰-q⁸+q⁴
```
