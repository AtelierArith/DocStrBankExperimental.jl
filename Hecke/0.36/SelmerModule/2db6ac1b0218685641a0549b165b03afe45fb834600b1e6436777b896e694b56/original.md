```
pselmer_group_fac_elem(p::Int, S::Vector{<:Integer}; algo::Symbol = :raw, check::Bool = true)
```

The Selmer group of Q - with the elements in factored form. For $p=2$, $-1$ can be included into $S$.

# Example

```jldoctest
julia> k, a = wildanger_field(3, 13);

julia> zk = maximal_order(k);

julia> S = collect(keys(factor(6*zk)));

julia> Sel, map = pselmer_group_fac_elem(2, S);

julia> sel, mmap = pselmer_group_fac_elem(2, [-1, 2, 3]);

julia> h = hom(Sel, sel, [preimage(mmap, Hecke.factored_norm(map(g), parent = codomain(mmap))) for g = gens(Sel)]);

julia> k, mk = kernel(h);

```
