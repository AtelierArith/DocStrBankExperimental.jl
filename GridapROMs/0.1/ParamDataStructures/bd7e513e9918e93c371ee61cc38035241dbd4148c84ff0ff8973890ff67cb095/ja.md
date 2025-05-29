```
struct TransientParamFunction{F,P,T} <: AbstractParamFunction{P}
  fun::F
  params::P
  times::T
end
```

一時的なパラメトリック空間を持つパラメトリック関数の表現。関数 `f : Ω₁ × ... × Ωₙ × D × [t₁,t₂]` が与えられたとき、ここで `[t₁,t₂]` は時間的な領域であり、`D` は `ParamSpace` であるか、同等に `f : Ω₁ × ... × Ωₙ × D × [t₁,t₂]` であり、ここで `D` は `TransientParamSpace` である。`(μ,t) ∈ D × [t₁,t₂]` における `f` の評価は、`Ω₁ × ... × Ωₙ` への `f` の制限を返す。
