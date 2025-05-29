```julia
DiscreteSystem(
    eqs::AbstractVector{<:Symbolics.Equation},
    iv,
    dvs,
    ps;
    controls,
    observed,
    systems,
    tspan,
    name,
    default_u0,
    default_p,
    defaults,
    preface,
    connector_type,
    metadata,
    gui_metadata,
    kwargs...
)

```

DiscreteSystemを構築します。
