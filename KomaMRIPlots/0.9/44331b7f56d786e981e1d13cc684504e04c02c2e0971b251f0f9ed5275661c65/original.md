```
p = plot_phantom_map(obj::Phantom, key::Symbol; kwargs...)
```

Plots a phantom map for a specific spin parameter given by `key`.

# Arguments

  * `obj`: (`::Phantom`) Phantom struct
  * `key`: (`::Symbol`, opts: [`:ρ`, `:T1`, `:T2`, `:T2s`, `:x`, `:y`, `:z`]) symbol for   displaying different parameters of the phantom spins

# Keywords

  * `height`: (`::Integer`, `=600`) plot height
  * `width`: (`::Integer`, `=nothing`) plot width
  * `darkmode`: (`::Bool`, `=false`) boolean to indicate whether to display darkmode style
  * `view_2d`: (`::Bool`, `=false`) boolean to indicate whether to use a 2D scatter plot
  * `colorbar`: (`::Bool`, `=true`) boolean to indicate whether to display a colorbar
  * `max_spins`:(`::Int`, `=100_000`) maximum number of displayed spins
  * `time_samples`:(`::Int`, `=0`) intermediate time samples between motion `t_start` and `t_end`
  * `frame_duration_ms`:(`::Int`, `=250`) time in miliseconds between two frames

# Returns

  * `p`: (`::PlotlyJS.SyncPlot`) plot of the phantom map for a specific spin parameter

# References

Colormaps from https://github.com/markgriswold/MRFColormaps Towards Unified Colormaps for Quantitative MRF Data, Mark Griswold, et al. (2018).

# Examples

```julia-repl
julia> obj2D, obj3D = brain_phantom2D(), brain_phantom3D();

julia> plot_phantom_map(obj2D, :ρ)

julia> plot_phantom_map(obj3D, :ρ)
```
