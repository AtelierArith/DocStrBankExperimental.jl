```julia
sitegroup(
    sg::Crystalline.SpaceGroup{D},
    wp::Crystalline.WyckoffPosition{D}
) -> Crystalline.SiteGroup

```

Return the site symmetry group `g::SiteGroup` for a Wyckoff position `wp` in space group `sg` (or with space group number `sgnum`; in this case, the dimensionality is inferred from `wp`).

`g` is a group of operations that are isomorphic to the those listed in `sg` (in the sense that they might differ by lattice vectors) and that leave the Wyckoff position `wp` invariant, such that `all(op -> wp == compose(op, wp), g) == true`.

The returned `SiteGroup` also contains the coset representatives of the Wyckoff position (that are again isomorphic to those featured in `sg`), accessible via [`cosets`](@ref), which e.g. generate the orbit of the Wyckoff position (see [`orbit(::SiteGroup)`](@ref)) and define a left-coset decomposition of `sg` jointly with the elements in `g`.

## Example

```jldoctest sitegroup
julia> sgnum = 16;

julia> D = 2;

julia> wp = wyckoffs(sgnum, D)[3] # pick a Wyckoff position
2b: [1/3, 2/3]

julia> sg = spacegroup(sgnum, D);

julia> g  = sitegroup(sg, wp)
SiteGroup{2} ⋕16 (p6) at 2b = [1/3, 2/3] with 3 operations:
 1
 {3⁺|1,1}
 {3⁻|0,1}
```

The group structure of a `SiteGroup` can be inspected with `MultTable`:

```jldoctest sitegroup
julia> MultTable(g)
3×3 MultTable{SymOperation{2}}:
──────────┬──────────────────────────────
          │        1  {3⁺|1,1}  {3⁻|0,1} 
──────────┼──────────────────────────────
        1 │        1  {3⁺|1,1}  {3⁻|0,1} 
 {3⁺|1,1} │ {3⁺|1,1}  {3⁻|0,1}         1
 {3⁻|0,1} │ {3⁻|0,1}         1  {3⁺|1,1}
──────────┴──────────────────────────────
```

The original space group can be reconstructed from a left-coset decomposition, using the operations and cosets contained in a `SiteGroup`:

```jldoctest sitegroup
julia> ops = [opʰ*opᵍ for opʰ in cosets(g) for opᵍ in g];

julia> Set(sg) == Set(ops)
true
```

## Terminology

Mathematically, the site symmetry group is a *stabilizer group* for a Wyckoff position, in the same sense that the little group of **k** is a stabilizer group for a **k**-point.

See also [`sitegroups`](@ref) for calculation of all site symmetry groups of a given space group.
