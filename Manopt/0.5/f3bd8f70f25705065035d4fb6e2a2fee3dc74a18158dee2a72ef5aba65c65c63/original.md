```
PrimalDualManifoldObjective{T<:AbstractEvaluationType} <: AbstractPrimalDualManifoldObjective{T}
```

Describes an Objective linearized or exact Chambolle-Pock algorithm, cf. [BergmannHerzogSilvaLouzeiroTenbrinckVidalNunez:2021](@cite), [ChambollePock:2011](@cite)

# Fields

All fields with `!!` can either be in-place or allocating functions, which should be set depending on the `evaluation=` keyword in the constructor and stored in `T <: AbstractEvaluationType`.

  * `cost`:                          $F + G(Λ(⋅))$ to evaluate interim cost function values
  * `linearized_forward_operator!!`: linearized operator for the forward operation in the algorithm $DΛ$
  * `linearized_adjoint_operator!!`: the adjoint differential $(DΛ)^* : \mathcal N → T\mathcal M$
  * `prox_f!!`:                      the proximal map belonging to $f$
  * `prox_G_dual!!`:                 the proximal map belonging to $g_n^*$
  * `Λ!!`:                           the  forward operator (if given) $Λ: \mathcal M → \mathcal N$

Either the linearized operator $DΛ$ or $Λ$ are required usually.

# Constructor

```
PrimalDualManifoldObjective(cost, prox_f, prox_G_dual, adjoint_linearized_operator;
    linearized_forward_operator::Union{Function,Missing}=missing,
    Λ::Union{Function,Missing}=missing,
    evaluation::AbstractEvaluationType=AllocatingEvaluation()
)
```

The last optional argument can be used to provide the 4 or 5 functions as allocating or mutating (in place computation) ones. Note that the first argument is always the manifold under consideration, the mutated one is the second.
