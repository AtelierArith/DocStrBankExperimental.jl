```julia
DiscreteSystem(
    eqs::AbstractVector{<:Symbolics.Equation},
    iv,
    dvs,
    ps;
    observed,
    systems,
    tspan,
    name,
    description,
    default_u0,
    default_p,
    guesses,
    initializesystem,
    initialization_eqs,
    defaults,
    preface,
    connector_type,
    parameter_dependencies,
    metadata,
    gui_metadata,
    kwargs...
)

```

DiscreteSystemを構築します。
