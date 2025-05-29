```
simulate_derivatives_finite_difference(
    requested_derivatives::Tuple{Vararg{Symbol}},
    echos::AbstractMatrix{<:Complex},
    sequence::BlochSimulator,
    parameters::StructVector{<:AbstractTissueProperties},
    stepsizes::T₁T₂B₁B₀=DEFAULT_STEPSIZES
)
```

Calculates the partial derivatives of pre-calculated echos (contained in `ctx`) with respect to the (non-linear) tissue properties in `requested_derivatives` using finite differences.

# Arguments

  * `requested_derivatives::Tuple{Vararg{Symbol}}`: A tuple with symbols corresponding to the (non-linear) tissue properties we want to compute partial derivatives for (e.g. (:T₁, :T₂, :B₁)).
  * `echos::AbstractMatrix`: Pre-computed matrix of magnetization at all echo times for all voxels.
  * `sequence::BlochSimulator`: The simulator representing the underlying MR pulse sequence.
  * `parameters::SimulationParameters`: The simulation parameters (in all voxels) used to generate `echos`.
  * `stepsizes::T₁T₂B₁B₀`: The step sizes for finite difference calculations for each of the different tissue properties. Default stepsizes are provided in `DEFAULT_STEPSIZES_FINITE_DIFFERENCE`.

# Returns

  * `∂echos`: A NamedTuple containing the partial derivatives of `ctx.echos` with respect to each of the `requested_derivatives`. That is, ∂echos.T₁ contains the partial derivatives w.r.t. T₁, ∂echos.T₂ contains the partial derivatives w.r.t. T₂, etc.

# Notes

  * We only calculate partial derivatives for non-linear tissue properties. For linear tissue properties (e.g. proton density) we need nothing more than `echos` itself.
