```
plot_SolSum(sol::Sol{T,O},xvars::Int...;interp=0.0001,note=" "::String,xlims=(0.0,0.0)::Tuple{Float64, Float64},ylims=(0.0,0.0)::Tuple{Float64, Float64},legend=:true::Bool) where{T,O}
```

plots of the sum of the variables xvars.

# Arguments

  * `sol::Sol{T,O}`: The solution struct.
  * `xvars::Int...`: The indices of the variables to sum. If no indices are provided, all variables are summed.
  * `interp::Float64`: The interpolation step.
  * `note::String`: A note to add to the title of the plot.
  * `xlims::Tuple{Float64, Float64}`: The x-axis limits of the plot.
  * `ylims::Tuple{Float64, Float64}`: The y-axis limits of the plot.
  * `legend::Bool`: A boolean indicating whether to display the legend.
