```
siteirreps(sitegroup::SiteGroup; mulliken::Bool=false]) --> Vector{PGIrrep}
```

Return the site symmetry irreps associated with the provided `SiteGroup`, obtained from a search over isomorphic point groups. The `SiteIrrep`s are in general a permutation of the irreps of the associated isomorphic point group.

By default, the labels of the site symmetry irreps are given in the CDML notation; to use the Mulliken notation, set the keyword argument `mulliken` to `true` (default, `false`).

## Example

```jldoctest
julia> sgnum = 16;

julia> sg = spacegroup(sgnum, 2);

julia> wp = wyckoffs(sgnum, 2)[3] # pick the third Wyckoff position
2b: [1/3, 2/3]

julia> siteg = sitegroup(sg, wp)
SiteGroup{2} ⋕16 (p6) at 2b = [1/3, 2/3] with 3 operations:
 1
 {3⁺|1,1}
 {3⁻|0,1}

julia> siteirs = siteirreps(siteg)
3-element Collection{SiteIrrep{2}} for ⋕16 (p6) at 2b = [1/3, 2/3]:
Γ₁┌        1: 1
  ├ {3⁺|1,1}: 1
  └ {3⁻|0,1}: 1

Γ₂┌        1: 1
  ├ {3⁺|1,1}: exp(0.6667iπ)
  └ {3⁻|0,1}: exp(-0.6667iπ)

Γ₃┌        1: 1
  ├ {3⁺|1,1}: exp(-0.6667iπ)
  └ {3⁻|0,1}: exp(0.6667iπ)
```
