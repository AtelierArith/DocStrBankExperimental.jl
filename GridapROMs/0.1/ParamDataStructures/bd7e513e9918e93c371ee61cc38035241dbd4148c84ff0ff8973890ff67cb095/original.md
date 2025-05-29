```
struct TransientParamFunction{F,P,T} <: AbstractParamFunction{P}
  fun::F
  params::P
  times::T
end
```

Representation of parametric functions with domain a transient parametric space. Given a function `f : Ω₁ × ... × Ωₙ × D × [t₁,t₂]`, where `[t₁,t₂]` is a temporal domain and `D` is a `ParamSpace`, or equivalently `f : Ω₁ × ... × Ωₙ × D × [t₁,t₂]`, where `D` is a `TransientParamSpace`, the evaluation of `f` in `(μ,t) ∈ D × [t₁,t₂]` returns the restriction of `f` to `Ω₁ × ... × Ωₙ`
