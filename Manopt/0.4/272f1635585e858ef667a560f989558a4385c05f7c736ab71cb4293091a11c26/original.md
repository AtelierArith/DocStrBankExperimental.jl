```
ConjugateGradientBealeRestart <: DirectionUpdateRule
```

An update rule might require a restart, that is using pure gradient as descent direction, if the last two gradients are nearly orthogonal, see [HagerZhang:2006; page 12](@cite) (in the preprint, page 46 in Journal page numbers). This method is named after E. Beale from his proceedings paper in 1972 [Beale:1972](@cite). This method acts as a *decorator* to any existing [`DirectionUpdateRule`](@ref) `direction_update`.

When obtain from the [`ConjugateGradientDescentState`](@ref)`cgs` the last $p_k,X_k$ and the current $p_{k+1},X_{k+1}$ iterate and the gradient, respectively.

Then a restart is performed, hence $β_k = 0$ returned if

$$
    \frac{ ⟨X_{k+1}, P_{p_{k+1}\gets p_k}X_k⟩}{\lVert X_k \rVert_{p_k}} > ξ,
$$

where $P_{a\gets b}(⋅)$ denotes a vector transport from the tangent space at $a$ to $b$, and $ξ$ is the `threshold`. The default threshold is chosen as `0.2` as recommended in [Powell:1977](@cite)

# Constructor

```
ConjugateGradientBealeRestart(
    direction_update::D,
    threshold=0.2;
    manifold::AbstractManifold = DefaultManifold(),
    vector_transport_method::V=default_vector_transport_method(manifold),
)
```
