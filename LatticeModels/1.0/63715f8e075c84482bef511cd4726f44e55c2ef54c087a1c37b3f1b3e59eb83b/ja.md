```
GenericLattice{SiteT}
```

`SiteT` サイトの一般的な格子。

## 例

```jldoctest
julia> using LatticeModels

julia> l = GenericLattice{2}()
0-site GenericLattice{GenericSite{2}} in 2D space

julia> push!(l, GenericSite(0, 0))  # (0, 0) にサイトを追加
1-site GenericLattice{GenericSite{2}} in 2D space:
  Site at [0.0, 0.0]

julia> push!(l, (0, 1))             # (0, 1) にサイトを追加
2-site GenericLattice{GenericSite{2}} in 2D space:
  Site at [0.0, 0.0]
  Site at [0.0, 1.0]

julia> push!(l, [1, 0])             # (1, 0) にサイトを追加
3-site GenericLattice{GenericSite{2}} in 2D space:
  Site at [0.0, 0.0]
  Site at [0.0, 1.0]
  Site at [1.0, 0.0]

julia> l[2]
2-dim GenericSite{2} at [0.0, 1.0]
```
