```
struct ParamFunction{F,P} <: AbstractParamFunction{P}
  fun::F
  params::P
end
```

Representation of parametric functions with domain a parametric space. Given a function `f` : Ω₁ × ... × Ωₙ × D, where D is a `ParamSpace`, the evaluation of `f` in `μ ∈ D` returns the restriction of `f` to Ω₁ × ... × Ωₙ
