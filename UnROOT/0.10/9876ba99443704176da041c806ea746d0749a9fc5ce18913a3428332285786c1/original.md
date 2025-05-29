```
LazyTree(f::ROOTFile, s::AbstractString, branch::Union{AbstractString, Regex})
LazyTree(f::ROOTFile, s::AbstractString, branch::Vector{Union{AbstractString, Regex}})
```

Constructor for `LazyTree`, which is close to an `DataFrame` (interface wise), and a lazy Table (speed wise). Looping over a `LazyTree` is fast and type stable. Internally, `LazyTree` contains a typed table whose branch are [`LazyBranch`](@ref). This means that at any given time only `N` baskets are cached, where `N` is the number of branches.

!!! note
    Accessing with `[start:stop]` will return a `LazyTree` with concrete internal table.


!!! warning
    Split branches are re-named, and the exact renaming may change. See  [Issue 156](https://github.com/JuliaHEP/UnROOT.jl/pull/156) for context.


# Example

```julia
julia> mytree = LazyTree(f, "Events", ["Electron_dxy", "nMuon", r"Muon_(pt|eta)$"])
 Row │ Electron_dxy     nMuon   Muon_eta         Muon_pt
     │ Vector{Float32}  UInt32  Vector{Float32}  Vector{Float32}
─────┼───────────────────────────────────────────────────────────
 1   │ [0.000371]       0       []               []
 2   │ [-0.00982]       2       [0.53, 0.229]    [19.9, 15.3]
 3   │ []               0       []               []
 4   │ [-0.00157]       0       []               []
 ⋮   │     ⋮            ⋮             ⋮                ⋮
```
