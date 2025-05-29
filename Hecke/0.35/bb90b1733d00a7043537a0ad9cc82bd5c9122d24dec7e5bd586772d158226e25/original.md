```
cyclotomic_units_totally_real(K::NumField)
```

Given the maximal totally real subfield $K$ of a cyclotomic field of prime conductor, return a generating set for the cyclotomic units of $K$.

# Examples

```jldoctest
julia> K, a = cyclotomic_real_subfield(7);

julia> cyclotomic_units_totally_real(K)
3-element Vector{AbsSimpleNumFieldElem}:
 -1
 (z_7 + 1/z_7)^2 - 1
 -(z_7 + 1/z_7)^2 - (z_7 + 1/z_7) + 2
```
