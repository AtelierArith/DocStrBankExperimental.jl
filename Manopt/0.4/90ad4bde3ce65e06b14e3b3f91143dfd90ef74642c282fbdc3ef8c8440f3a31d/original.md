```
DaiYuanCoefficient <: DirectionUpdateRule
```

Computes an update coefficient for the conjugate gradient method, where the [`ConjugateGradientDescentState`](@ref)`cgds` include the last iterates $p_k,X_k$, the current iterates $p_{k+1},X_{k+1}$ of the iterate and the gradient, respectively, and the last update direction $\delta=\delta_k$, based on [DaiYuan:1999](@cite) adapted to manifolds:

Let $\nu_k = X_{k+1} - P_{p_{k+1}\gets p_k}X_k$, where $P_{a\gets b}(⋅)$ denotes a vector transport from the tangent space at $a$ to $b$.

Then the coefficient reads

$$
β_k =
\frac{ \lVert X_{k+1} \rVert_{p_{k+1}}^2 }
{\langle P_{p_{k+1}\gets p_k}\delta_k, \nu_k \rangle_{p_{k+1}}}.
$$

See also [`conjugate_gradient_descent`](@ref)

# Constructor

```
function DaiYuanCoefficient(
    M::AbstractManifold=DefaultManifold(2);
    t::AbstractVectorTransportMethod=default_vector_transport_method(M)
)
```

Construct the Dai—Yuan coefficient update rule, where the parallel transport is the default vector transport and a new storage is created by default.
