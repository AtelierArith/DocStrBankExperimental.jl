```
ROOTFile(filename::AbstractString; customstructs = Dict("TLorentzVector" => LorentzVector{Float64}))
```

`ROOTFile`'s constructor from a file. The `customstructs` dictionary can be used to pass user-defined struct as value and its corresponding `fClassName` (in Branch) as key such that `UnROOT` will know to interpret them, see [`interped_data`](@ref).

See also: [`LazyTree`](@ref), [`LazyBranch`](@ref)

# Example

```julia
julia> f = ROOTFile("test/samples/NanoAODv5_sample.root")
ROOTFile with 2 entries and 21 streamers.
test/samples/NanoAODv5_sample.root
└─ Events
   ├─ "run"
   ├─ "luminosityBlock"
   ├─ "event"
   ├─ "HTXS_Higgs_pt"
   ├─ "HTXS_Higgs_y"
   └─ "⋮"
```
