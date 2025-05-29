```julia
get_nonnegativity_auxilliary_variables(𝓂)

```

Returns the auxilliary variables, without timing subscripts, added to the non-stochastic steady state problem because certain expression cannot be negative (e.g. given `log(c/q)` an auxilliary variable is created for `c/q`).

See `get_steady_state_equations` for more details on the auxilliary variables and equations.

# Arguments

  * `𝓂`: object created by [`@model`](@ref) and [`@parameters`](@ref).

# Returns

  * `Vector{String}` of the auxilliary parameters.

# Examples

```jldoctest
using MacroModelling

@model RBC begin
    1  /  c[0] = (β  /  c[1]) * (α * exp(z{TFP}[1]) * k[0]^(α - 1) + (1 - exp(z{δ}[1]) * δ))
    c[0] + k[0] = (1 - exp(z{δ}[0])δ) * k[-1] + q[0]
    q[0] = exp(z{TFP}[0]) * k[-1]^α
    for shock in [TFP, δ]
        z{shock}[0] = ρ{shock} * z{shock}[-1] + σ{shock} * (eps{shock}[x] + eps_news{shock}[x-1])
    end
    Δc_share[0] = log(c[0]/q[0]) - log(c[-1]/q[-1])
    Δk_4q[0] = log(k[0]) - log(k[-4])
end

@parameters RBC begin
    σ = 0.01
    ρ = 0.2
    capital_to_output = 1.5
    k[ss] / (4 * q[ss]) = capital_to_output | δ
    alpha = .5
    α = alpha
    β = 0.95
end

get_nonnegativity_auxilliary_variables(RBC)
# output
2-element Vector{String}:
 "➕₁"
 "➕₂"
```
