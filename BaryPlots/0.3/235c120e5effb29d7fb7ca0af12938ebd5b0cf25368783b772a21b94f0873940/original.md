```
plot_evolution(
    payoff_functions::Tuple{Function, Function, Function},
    x0_list::Vector{<:AbstractVector{<:Real}},
    tspan::Tuple{Float64, Float64};
    labels::Vector{String} = ["Strategy 1", "Strategy 2", "Strategy 3"],
    extra_params::NamedTuple = NamedTuple(),
    steady_state_tol::Float64 = 1e-6,
    arrow_list::Vector{Vector{Int}} = Vector{Vector{Int}}(),
    trajectory_labels::Vector{String} = String[],
    trajectory_colors::AbstractVector = Any[],
    trajectory_linewidth::Int = 2,
    num_initial_guesses::Int = 1000,
    solver_tol::Float64 = 1e-8,
    equilibrium_tol::Float64 = 1e-5,
    validity_tol::Float64 = 1e-6,
    stability_tol::Float64 = 1e-6,
    markersize::Int = 9,
    markerstrokewidth::Int = 2,
    colored_trajectories::Bool = false,
    contour::Bool = false,
    contour_color::Symbol = :roma,
    contour_resolution::Int = 150,
    contour_levels::Int = 10,
    colorbar::Bool = false,
    triangle_linewidth::Int = 2,
    legend::Bool = false,
    margin::Int = 2,
    dpi::Int = 300,
)::Plots.Plot
```

Simulates replicator dynamics trajectories within a 3-strategy simplex, locates equilibria, and creates a ternary plot of the results.

# Arguments

  * `payoff_functions`: A tuple of three payoff functions `(payoff1, payoff2, payoff3)`, each accepting `(x, t, params)` where `x` is the normalized frequency vector.
  * `x0_list`: A collection of initial conditions in the simplex (each a length-3 vector). Each trajectory is simulated from these initial points.
  * `tspan`: A tuple `(tstart, tfinal)` specifying the integration window.
  * `labels`: Labels for the triangle corners. Default is `["Strategy 1", "Strategy 2", "Strategy 3"]`.
  * `extra_params`: Additional parameters passed to the payoff functions, packaged in a `NamedTuple`.
  * `steady_state_tol`: If the norm of the derivative falls below this threshold, the solver stops early (via a callback).
  * `arrow_list`: An array-of-arrays specifying indices at which to draw an arrow along each trajectory.
  * `trajectory_labels`: Labels for each trajectory if you want a legend. Defaults to "Trajectory i" for i in `1:length(x0_list)`.
  * `trajectory_colors`: Colors for trajectories. If empty, defaults to black for all or a tab10 palette if `colored_trajectories` is true.
  * `trajectory_linewidth`: Width of the lines used for plotting trajectories.
  * `num_initial_guesses`: Number of random initial guesses for root-finding to locate equilibria.
  * `solver_tol`: Tolerance used internally by the nonlinear solver for equilibrium-finding.
  * `equilibrium_tol`: Tolerance for declaring two equilibria to be effectively the same.
  * `validity_tol`: Tolerance for points to be considered inside the simplex (0 ≤ xᵢ ≤ 1).
  * `stability_tol`: Tolerance used when deciding if all eigenvalues have negative real parts (stable).
  * `markersize`: Size of equilibrium markers.
  * `markerstrokewidth`: Stroke width of the equilibrium marker boundary.
  * `colored_trajectories`: If `true`, color each trajectory differently using a color palette; otherwise, use a single color.
  * `contour`: Whether to overlay a contour plot of average payoffs. If `true`, uses `scatter` to color each simplex grid point by its average payoff.
  * `contour_color`: A symbol representing the color gradient (e.g. `:viridis`, `:roma`) for the contour plot.
  * `contour_resolution`: Resolution of the simplex grid for contour plotting.
  * `contour_levels`: Number of contour levels to display (used in color scaling).
  * `colorbar`: Whether to display a color bar when `contour` is `true`.
  * `triangle_linewidth`: Line width for the simplex boundary lines.
  * `legend`: Whether to display a legend for trajectory labels.
  * `margin`: How many rows/columns of the simplex grid to skip from the edges when computing and plotting contour points (avoid overlapping boundaries).
  * `dpi`: Resolution for the final plot.

# Returns

  * A `Plots.Plot` object with:

    1. An (optional) contour plot of average payoffs in the simplex.
    2. Ternary simplex edges (with neutral edges optionally highlighted).
    3. Simulated trajectories from the provided initial conditions.
    4. Detected equilibria, marked as filled circles if stable or hollow circles if unstable.

# Notes

  * Internally calls `identify_neutral_edges` to highlight edges where payoffs between two strategies are equal for all points along that edge.
  * Equilibria are located with `find_equilibria`, and each one is tested for stability by analyzing the Jacobian.
  * The arrow drawing is handled by `arrow0!`, with user-specified arrow positions in `arrow_list`.
