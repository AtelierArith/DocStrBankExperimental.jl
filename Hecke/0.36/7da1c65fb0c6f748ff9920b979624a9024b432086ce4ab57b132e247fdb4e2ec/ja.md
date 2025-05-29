```
grunwald_wang(dp::Dict{<:NumFieldOrderIdeal, Int})
grunwald_wang(dp::Dict{<:NumFieldOrderIdeal, Int}, di::Dict{<:NumFieldEmb, Int})
```

イデアルをキーとする `dp` で与えられた場所のコレクションと、キーとして埋め込みを持つ `di` で与えられた場所に対して、辞書の値としての次数を持つ巡回拡張を見つけます。

次数はローカル次数（値）の `lcm` になります。拡張は `dp` の場所で非分岐であり、`2` 以上の素数が関与しない限りです。

この体は `ray_class_field` として構成されます。

# 例

```julia
julia> A = grunwald_wang(Dict(3*ZZ => 3, 5*ZZ => 2))
Class field defined mod (<13, 13>, InfPlc{AbsSimpleNumField, AbsSimpleNumFieldEmbedding}[]) of structure Abelian group with structure: Z/6

julia> K = absolute_simple_field(number_field(A))[1];

julia> prime_decomposition_type(maximal_order(K), 5)
3-element Vector{Tuple{Int64, Int64}}:
 (2, 1)
 (2, 1)
 (2, 1)


julia> prime_decomposition_type(maximal_order(K), 3)
2-element Vector{Tuple{Int64, Int64}}:
 (3, 1)
 (3, 1)

```
