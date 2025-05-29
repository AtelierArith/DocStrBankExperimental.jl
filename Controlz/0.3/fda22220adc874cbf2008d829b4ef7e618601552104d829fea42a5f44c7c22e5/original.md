```
viz_response(data, 
             title="", xlabel="time, t", 
             ylabel="output, y*(t)",
             savename=nothing)
```

plot `data[:, :output]` vs. `data[:, :t]` to visualize the response of a system to an input.  typically the data frame, `data`, is returned from [`simulate`](@ref).

# Arguments

  * `data::DataFrame`: data frame of time series data, containing a `:t` column for times and `:output` column for the outputs.
  * `title::String`: title of plot
  * `xlabel::String`: x-label
  * `ylabel::String`: y-label
  * `savename::Union{Nothing, String}`: filename to save as a figure in .png format.

# Returns

`CairoMakie.jl` `Figure` object. this will display in a Pluto.jl notebook.

`CairoMakie.jl` commands can be invoked after `viz_response` to make further changes to the figure panel by e.g.:

```julia
fig = viz_response(data)
ax = current_axis(fig)
ax.xlabel = "new xlabel"
xlims!(ax, 0, 15)
```

# Example

```
g = 4 / (4 * s ^ 2 + 0.8 * s + 1)
U = 1 / s
Y = g * U
data = simulate(Y, 50.0)
fig = viz_response(data)
```
