```
unitary_geodesic(
    operator::EmbeddedOperator,
    samples::Int;
    kwargs...
)

unitary_geodesic(
    U_goal::AbstractMatrix{<:Number},
    samples::Int;
    kwargs...
)

unitary_geodesic(
    U₀::AbstractMatrix{<:Number},
    U₁::AbstractMatrix{<:Number},
    samples::Number;
    kwargs...
)

unitary_geodesic(
    U₀::AbstractMatrix{<:Number},
    U₁::AbstractMatrix{<:Number},
    timesteps::AbstractVector{<:Number};
    return_generator=false
)
```

Compute a geodesic connecting two unitary operators.
