```julia
direct_transcription(
    ocp::CTModels.Model,
    description...;
    grid_size,
    disc_method,
    time_grid,
    init,
    adnlp_backend,
    solver_backend,
    show_time,
    matrix_free
) -> Tuple{CTDirect.DOCP{_A, CTModels.Model{TimesModelType, StateModelType, ControlModelType, VariableModelType, DynamicsModelType, ObjectiveModelType, ConstraintsModelType}} where {_A<:CTDirect.Discretization, TimesModelType<:CTModels.AbstractTimesModel, StateModelType<:CTModels.AbstractStateModel, ControlModelType<:CTModels.AbstractControlModel, VariableModelType<:CTModels.AbstractVariableModel, DynamicsModelType<:Function, ObjectiveModelType<:CTModels.AbstractObjectiveModel, ConstraintsModelType<:CTModels.AbstractConstraintsModel}, ADNLPModels.ADNLPModel{Float64, Vector{Float64}, Vector{Int64}}}

```

Discretize an optimal control problem into a nonlinear optimization problem (ie direct transcription)

# Arguments

  * ocp: optimal control problem as defined in `CTModels`
  * [description]: can specifiy for instance the NLP model and / or solver (:ipopt, :madnlp or :knitro)

# Keyword arguments (optional)

  * `grid_size`: number of time steps for the discretized problem ([250])
  * `disc_method`: discretization method ([`:trapeze`], `:euler`, `:euler_implicit`, `:midpoint`, `gauss_legendre_2`, `gauss_legendre_3`)
  * `time_grid`: explicit time grid (can be non uniform)
  * `init`: info for the starting guess (values as named tuple or existing solution)
  * `adnlp_backend`: backend for automatic differentiation in ADNLPModels ([`:optimized`], `:manual`, `:default`)
  * show_time: (:true, [:false]) show timing details from ADNLPModels
