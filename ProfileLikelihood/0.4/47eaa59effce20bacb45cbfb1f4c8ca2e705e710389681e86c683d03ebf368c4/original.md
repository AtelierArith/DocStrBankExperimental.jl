```
plot_profiles(prof::ProfileLikelihoodSolution, vars = profiled_parameters(prof); 
    ncol=nothing, 
    nrow=nothing,
    true_vals=Dict(vars .=> nothing), 
    spline=true, 
    show_mles=true, 
    shade_ci=true, 
    fig_kwargs=nothing, 
    axis_kwargs=nothing,
    show_points=false,
    markersize=9,
    latex_names=default_latex_names(prof, vars),
    xlim_tuples=nothing,
    ylim_tuples=nothing)
```

Plot results from a profile likelihood solution `prof`. To use this function you you need to have done `using CairoMakie` (or any other Makie backend).

# Arguments

  * `prof::ProfileLikelihoodSolution`: The profile likelihood solution from [`profile`](@ref).
  * `vars = profiled_parameters(prof)`: The parameters to plot.

# Keyword Arguments

  * `ncol=nothing`: The number of columns to use. If `nothing`, chosen automatically via `choose_grid_layout`.
  * `nrow=nothing`: The number of rows to use. If `nothing`, chosen automatically via `choose_grid_layout`
  * `true_vals=Dict(vars .=> nothing)`: A dictionary mapping parameter indices to their true values, if they exist. If `nothing`, nothing is plotted, otherwise a black line is plotted at the true value for the profile.
  * `spline=true`: Whether the curve plotted should come from a spline through the results, or if the data itself should be plotted.
  * `show_mles=true`: Whether to put a red line at the MLEs.
  * `shade_ci=true`: Whether to shade the area under the profile between the confidence interval.
  * `fig_kwargs=nothing`: Extra keyword arguments for `Figure` (see the Makie docs).
  * `axis_kwargs=nothing`: Extra keyword arguments for `Axis` (see the Makie docs).
  * `show_points=false`: Whether to show the profile data.
  * `markersize=9`: The marker size used for `show_points`.
  * `latex_names=default_latex_names(prof, vars)`: LaTeX names to use for the parameters. Defaults to the `syms` names. (There may be issues with the generated LaTeX for more esoteric names. Make an issue if needed.)
  * `xlim_tuples=nothing`: `xlims` to use for each plot. `nothing` if the `xlims` should be set automatically.
  * `ylim_tuples=nothing`: `ylims` to use for each plot. `nothing` if the `ylims` should be set automatically.

# Output

The `Figure()` is returned.

---

```
plot_profiles(prof::BivariateProfileLikelihoodSolution, vars = profiled_parameters(prof); 
    ncol=nothing,
    nrow=nothing,
    true_vals=Dict(1:number_of_parameters(get_likelihood_problem(prof)) .=> nothing),
    show_mles=true,
    fig_kwargs=nothing,
    axis_kwargs=nothing,
    interpolation=false,
    smooth_confidence_boundary=false,
    close_contour=true,
    latex_names=default_latex_names(prof, vars),
    xlim_tuples=nothing,
    ylim_tuples=nothing)
```

Plot results from a bivariate profile likelihood solution `prof`. To use this function you need to have done `using CairoMakie` (or any other Makie backend).

# Arguments

  * `prof::ProfileLikelihoodSolution`: The profile likelihood solution from [`profile`](@ref).
  * `vars = profiled_parameters(prof)`: The parameters to plot.

# Keyword Arguments

  * `ncol=nothing`: The number of columns to use. If `nothing`, chosen automatically via `choose_grid_layout`.
  * `nrow=nothing`: The number of rows to use. If `nothing`, chosen automatically via `choose_grid_layout`
  * `true_vals=Dict(1:number_of_parameters(get_likelihood_problem(prof)) .=> nothing)`: A dictionary mapping parameter indices to their true values, if they exist. If `nothing`, nothing is plotted, otherwise a black dot is plotted at the true value on the bivariate profile's plot.
  * `show_mles=true`: Whether to put a red dot at the MLEs.
  * `fig_kwargs=nothing`: Extra keyword arguments for `Figure` (see the Makie docs).
  * `axis_kwargs=nothing`: Extra keyword arguments for `Axis` (see the Makie docs).
  * `interpolation=false`: Whether to plot the profile using the interpolant (`true`), or to use the data from `prof` directly (`false`).
  * `smooth_confidence_boundary=false`: Whether to smooth the confidence region boundary when plotting (`true`) or not (`false`). The smoothing is done with a spline.
  * `close_contour=true`: Whether to connect the last part of the confidence region boundary to the beginning (`true`) or not (`false`).
  * `latex_names=default_latex_names(prof, vars)`: LaTeX names to use for the parameters. Defaults to the `syms` names. (There may be issues with the generated LaTeX for more esoteric names. Make an issue if needed.)
  * `xlim_tuples=nothing`: `xlims` to use for each plot. `nothing` if the `xlims` should be set automatically.
  * `ylim_tuples=nothing`: `ylims` to use for each plot. `nothing` if the `ylims` should be set automatically.

# Output

The `Figure()` is returned.
