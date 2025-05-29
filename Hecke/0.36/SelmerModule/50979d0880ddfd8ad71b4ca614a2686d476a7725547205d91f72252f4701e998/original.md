```
pselmer_group_fac_elem(p::Int, S::Vector{<:AbsNumFieldOrderIdeal{AbsSimpleNumField, AbsSimpleNumFieldElem}}; check::Bool = true, algo::Symbol = :raw)
```

Let $K$ be the number field of the prime ideals in $S$. Then the $p$-Selmer group is a subgroup of $K^*$ modulo $p$-th powers of elements such that all valuations outside $S$ are divisible by $p$.

This parametrises the maximal radical $p$-extension unramified outside $S$.

In this version, the eelements are returned in factored form. The `algo` parameter can be set to `:raw` or `:compRep`, in the latter case, the representatives will be reduced modulo $p$-th powers. The support of the principl ideal can be random though.

`check` controls if the pre-image map tests if the elements are actually in the codomain.

See also `pselmer_group`

# Example

```jldoctest
julia> k, a = wildanger_field(3, 13);

julia> zk = maximal_order(k);

julia> S = collect(keys(factor(6*zk)));

julia> Sel, map = pselmer_group_fac_elem(2, S);

julia> g = evaluate(map(Sel[3]));

julia> K, _ = radical_extension(2, g);

julia> ZK = maximal_order(K);

julia> issubset(Set(keys(factor(discriminant(ZK)))) , S)
true

```
