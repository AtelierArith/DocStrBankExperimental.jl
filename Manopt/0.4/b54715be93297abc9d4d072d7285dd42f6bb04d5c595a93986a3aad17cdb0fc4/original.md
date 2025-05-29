```
FletcherReevesCoefficient <: DirectionUpdateRule
```

Computes an update coefficient for the conjugate gradient method, where the [`ConjugateGradientDescentState`](@ref)`cgds` include the last iterates $p_k,X_k$, the current iterates $p_{k+1},X_{k+1}$ of the iterate and the gradient, respectively, and the last update direction $\delta=\delta_k$,  based on [FletcherReeves:1964](@cite) adapted to manifolds:

$$
β_k =
\frac{\lVert X_{k+1}\rVert_{p_{k+1}}^2}{\lVert X_k\rVert_{x_{k}}^2}.
$$

See also [`conjugate_gradient_descent`](@ref)

# Constructor

```
FletcherReevesCoefficient(a::StoreStateAction=())
```

Construct the Fletcher—Reeves coefficient update rule, a new storage is created by default.
