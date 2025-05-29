```
ConjugateDescentCoefficient <: DirectionUpdateRule
```

Computes an update coefficient for the conjugate gradient method, where the [`ConjugateGradientDescentState`](@ref)`cgds` include the last iterates $p_k,X_k$, the current iterates $p_{k+1},X_{k+1}$ of the iterate and the gradient, respectively, and the last update direction $\delta=\delta_k$,  based on [Fletcher:1987](@cite) adapted to manifolds:

$$
β_k =
\frac{ \lVert X_{k+1} \rVert_{p_{k+1}}^2 }
{\langle -\delta_k,X_k \rangle_{p_k}}.
$$

See also [`conjugate_gradient_descent`](@ref)

# Constructor

```
ConjugateDescentCoefficient(a::StoreStateAction=())
```

Construct the conjugate descent coefficient update rule, a new storage is created by default.
