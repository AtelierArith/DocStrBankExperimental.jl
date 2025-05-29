```julia
wyckoffs(
    sgnum::Integer
) -> Vector{Crystalline.WyckoffPosition{3}}
wyckoffs(sgnum::Integer, ::Val{D}) -> Any

```

Return the Wyckoff positions of space group `sgnum` in dimension `D` as a  `Vector{WyckoffPosition{D}`.

The positions are given in the conventional basis setting, following the conventions of the Bilbao Crystallographic Server (from which the underlying data is sourced [^1]).

## Example

```jldoctest
julia> wps = wyckoffs(16, 2)
4-element Vector{WyckoffPosition{2}}:
 6d: [α, β]
 3c: [1/2, 0]
 2b: [1/3, 2/3]
 1a: [0, 0]
```

## References

[^1]: Aroyo, *et al.*,   [Z. Kristallogr. **221**, 15-27 (2006)](https://doi.org/0.1524/zkri.2006.221.1.15)
