```julia
struct VortexFilament{TV<:(AbstractVector{<:AbstractVector}), TI<:AbstractVector{Int64}}
```

Defines a vortex filament of strength `Γ`, discretized by vertices in `vertices` and segments in `segments`, which connect the vertices. Each segment in `segments` should connect two subsequent entries of `vertices`. A vertex can be marked as a bound (e.g. to a wing) if its index appears in `boundidx`. Similarly, a vortex is marked as a free vertex if its index appears in `freeidx`.

# Fields

  * `Γ`: Γ: Strength of the vortex filament.
  * `vertices`: vertices: Array of vertices of the vortex filament.
  * `segments`: segments: Array of segments of the vortex filament.
  * `freeidx`: freeidx: Array of indices of the free vertices of the vortex filament.
  * `boundidx`: boundidx: Array of indices of the bound vertices of the vortex filament.
