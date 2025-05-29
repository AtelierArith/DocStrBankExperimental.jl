```julia
ExpectationProblem(S, g, h, pdist, params)
ExpectationProblem(g, pdist, params)
ExpectationProblem(sm::SystemMap, g, h, d)
```

Defines ∫ g(S(h(x,u0,p)))*f(x)dx

## Arguments

Let 𝕏 = uncertainty space, 𝕌 = Initial condition space, ℙ = model parameter space

  * S: 𝕌 × ℙ → 𝕌 also known as system map.
  * g: 𝕌 × ℙ → ℝⁿᵒᵘᵗ also known as the observables or output function.
  * h: 𝕏 × 𝕌 × ℙ → 𝕌 × ℙ also known as covariate function.
  * pdf(d,x): 𝕏 → ℝ the uncertainty distribution of the initial states.
  * params
