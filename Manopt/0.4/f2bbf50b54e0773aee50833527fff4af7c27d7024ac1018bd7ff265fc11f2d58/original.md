```
PolakRibiereCoefficient <: DirectionUpdateRule
```

Computes an update coefficient for the conjugate gradient method, where the [`ConjugateGradientDescentState`](@ref)`cgds` include the last iterates $p_k,X_k$, the current iterates $p_{k+1},X_{k+1}$ of the iterate and the gradient, respectively, and the last update direction $\delta=\delta_k$,  based on [PolakRibiere:1969](@cite) and [Polyak:1969](@cite) adapted to manifolds:

Let $\nu_k = X_{k+1} - P_{p_{k+1}\gets p_k}X_k$, where $P_{a\gets b}(⋅)$ denotes a vector transport from the tangent space at $a$ to $b$.

Then the update reads

$$
β_k =
\frac{ \langle X_{k+1}, \nu_k \rangle_{p_{k+1}} }
{\lVert X_k \rVert_{p_k}^2 }.
$$

# Constructor

```
function PolakRibiereCoefficient(
    M::AbstractManifold=DefaultManifold(2);
    t::AbstractVectorTransportMethod=default_vector_transport_method(M)
)
```

Construct the PolakRibiere coefficient update rule, where the parallel transport is the default vector transport and a new storage is created by default.

See also [`conjugate_gradient_descent`](@ref)
