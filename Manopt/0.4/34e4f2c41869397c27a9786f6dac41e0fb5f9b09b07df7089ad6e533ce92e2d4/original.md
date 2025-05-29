```
HagerZhangCoefficient <: DirectionUpdateRule
```

Computes an update coefficient for the conjugate gradient method, where the [`ConjugateGradientDescentState`](@ref)`cgds` include the last iterates $p_k,X_k$, the current iterates $p_{k+1},X_{k+1}$ of the iterate and the gradient, respectively, and the last update direction $\delta=\delta_k$, based on [HagerZhang:2005](@cite). adapted to manifolds: let $\nu_k = X_{k+1} - P_{p_{k+1}\gets p_k}X_k$, where $P_{a\gets b}(⋅)$ denotes a vector transport from the tangent space at $a$ to $b$.

$$
β_k = \Bigl\langle\nu_k -
\frac{ 2\lVert \nu_k\rVert_{p_{k+1}}^2 }{ \langle P_{p_{k+1}\gets p_k}\delta_k, \nu_k \rangle_{p_{k+1}} }
P_{p_{k+1}\gets p_k}\delta_k,
\frac{X_{k+1}}{ \langle P_{p_{k+1}\gets p_k}\delta_k, \nu_k \rangle_{p_{k+1}} }
\Bigr\rangle_{p_{k+1}}.
$$

This method includes a numerical stability proposed by those authors.

See also [`conjugate_gradient_descent`](@ref)

# Constructor

```
function HagerZhangCoefficient(t::AbstractVectorTransportMethod)
function HagerZhangCoefficient(M::AbstractManifold = DefaultManifold(2))
```

Construct the Hager Zhang coefficient update rule, where the parallel transport is the default vector transport and a new storage is created by default.
