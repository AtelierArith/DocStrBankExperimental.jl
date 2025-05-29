```julia
get_jump_variables(𝓂)

```

Returns the jump variables of the model. Jump variables occur in the future and not in the past or occur in all three: past, present, and future.

In case programmatic model writing was used this function returns the parsed variables (see `z` in example).

# Arguments

  * `𝓂`: object created by [`@model`](@ref) and [`@parameters`](@ref).

# Returns

  * `Vector{String}` of the jump variables.

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

get_jump_variables(RBC)
# output
3-element Vector{String}:
 "c"
 "z{TFP}"
 "z{δ}"
```
