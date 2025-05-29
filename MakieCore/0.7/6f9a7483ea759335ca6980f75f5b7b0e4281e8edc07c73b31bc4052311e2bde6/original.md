```
Plot{PlotFunc}(args::Tuple, kw::Dict{Symbol, Any})
```

Creates a Plot corresponding to the recipe function `PlotFunc`. Each recipe defines an alias for `Plot{PlotFunc}`. Example:

```julia
const Scatter = Plot{scatter} # defined in the scatter recipe
Plot{scatter}((1:4,), Dict{Symbol, Any}(:color => :red)) isa Scatter
# Same as:
Scatter((1:4,), Dict{Symbol, Any}(:color => :red))
```
