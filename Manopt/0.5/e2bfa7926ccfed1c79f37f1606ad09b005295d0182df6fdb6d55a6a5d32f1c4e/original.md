```
ConstrainedProblem{
    TM <: AbstractManifold,
    O <: AbstractManifoldObjective
    HR<:Union{AbstractPowerRepresentation,Nothing},
    GR<:Union{AbstractPowerRepresentation,Nothing},
    HHR<:Union{AbstractPowerRepresentation,Nothing},
    GHR<:Union{AbstractPowerRepresentation,Nothing},
} <: AbstractManoptProblem{TM}
```

A constrained problem might feature different ranges for the (vectors of) gradients of the equality and inequality constraints.

The ranges are required in a few places to allocate memory and access elements correctly, they work as follows:

Assume the objective is

$$
\begin{aligned}
 \operatorname*{arg\,min}_{p ∈\mathcal{M}} & f(p)\\
 \text{subject to } &g_i(p)\leq0 \quad \text{ for all } i=1,…,m,\\
 \quad &h_j(p)=0 \quad \text{ for all } j=1,…,n.
\end{aligned}
$$

then the gradients can (classically) be considered as vectors of the components gradients, for example $\bigl(\operatorname{grad} g_1(p), \operatorname{grad} g_2(p), …, \operatorname{grad} g_m(p) \bigr)$.

In another interpretation, this can be considered a point on the tangent space at $P = (p,…,p) \in \mathcal M^m$, so in the tangent space to the [`PowerManifold`](@extref `ManifoldsBase.PowerManifold`) $\mathcal M^m$. The case where this is a [`NestedPowerRepresentation`](@extref `ManifoldsBase.NestedPowerRepresentation`) this agrees with the interpretation from before, but on power manifolds, more efficient representations exist.

To then access the elements, the range has to be specified. That is what this problem is for.

# Constructor

```
ConstrainedManoptProblem(
    M::AbstractManifold,
    co::ConstrainedManifoldObjective;
    range=NestedPowerRepresentation(),
    gradient_equality_range=range,
    gradient_inequality_range=range
    hessian_equality_range=range,
    hessian_inequality_range=range
)
```

Creates a constrained Manopt problem specifying an [`AbstractPowerRepresentation`](@extref `ManifoldsBase.AbstractPowerRepresentation`) for both the `gradient_equality_range` and the `gradient_inequality_range`, respectively.
