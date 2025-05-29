```
ribbon_scene(chain_backbones::AbstractVector{<:AbstractArray{T,3}}; backgroundcolor=:black, camcontrols=(;), kwargs...)
```

Render a protein as a ribbon diagram. The display will be automatically centered on the rendered ribbon, unless the user supplies `camcontrols` (see Makie's camera documentation for details).
