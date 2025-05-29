```
grunwald_wang(dp::Dict{<:NumFieldOrderIdeal, Int})
grunwald_wang(dp::Dict{<:NumFieldOrderIdeal, Int}, di::Dict{<:NumFieldEmb, Int})
```

For a collection of places given via ideals as keys of `dp` and embeddings given as keys of `di` find a cyclic extension where the completions at the places have the degrees as the values of the dictionaries.

The degree will be the `lcm` of the local degree (values), the extension will be unramified at the places in `dp` unless they involve primes above `2`.

The field will be constructed as a `ray_class_field`.

# EXAMPLES

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
