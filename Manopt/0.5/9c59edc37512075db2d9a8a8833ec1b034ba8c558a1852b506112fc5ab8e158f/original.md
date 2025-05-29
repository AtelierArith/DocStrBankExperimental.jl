```
ManifoldAlternatingGradientObjective{E<:AbstractEvaluationType,TCost,TGradient} <: AbstractManifoldGradientObjective{E}
```

An alternating gradient objective consists of

  * a cost function $F(x)$
  * a gradient $\operatorname{grad}F$ that is either

      * given as one function $\operatorname{grad}F$ returning a tangent vector `X` on `M` or
      * an array of gradient functions $\operatorname{grad}F_i$, `ì=1,…,n` s each returning a component of the gradient

    which might be allocating or mutating variants, but not a mix of both.

!!! note
    This Objective is usually defined using the `ProductManifold` from `Manifolds.jl`, so `Manifolds.jl` to be loaded.


# Constructors

```
ManifoldAlternatingGradientObjective(F, gradF::Function;
    evaluation=AllocatingEvaluation()
)
ManifoldAlternatingGradientObjective(F, gradF::AbstractVector{<:Function};
    evaluation=AllocatingEvaluation()
)
```

Create a alternating gradient problem with an optional `cost` and the gradient either as one function (returning an array) or a vector of functions.
