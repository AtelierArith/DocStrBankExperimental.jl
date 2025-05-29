find*pure*growth*slope(t, E, time*range=nothing)

Estimate an exponential fit of the form E ≈ E₀ * exp(γt).

Return `(line, γ)`, where     - `γ` is the best fit to the exponential growth rate,     - `line` is `E₀ * exp.(γ .* t)`.
