```
MomentumGradient <: DirectionUpdateRule
```

Append a momentum to a gradient processor, where the last direction and last iterate are stored and the new is composed as $η_i = m*η_{i-1}' - s d_i$, where $sd_i$ is the current (inner) direction and $η_{i-1}'$ is the vector transported last direction multiplied by momentum $m$.

# Fields

  * `p_old`:                   (`rand(M)`) remember the last iterate for parallel transporting the last direction
  * `momentum`:                (`0.2`) factor for momentum
  * `direction`:               internal [`DirectionUpdateRule`](@ref) to determine directions to add the momentum to.
  * `vector_transport_method`: (`default_vector_transport_method(M, typeof(p))`) vector transport method to use
  * `X_old`:                   (`zero_vector(M,x0)`) the last gradient/direction update added as momentum

# Constructors

Add momentum to a gradient problem, where by default just a gradient evaluation is used

```
MomentumGradient(
    M::AbstractManifold;
    p=rand(M),
    s::DirectionUpdateRule=IdentityUpdateRule();
    X=zero_vector(p.M, x0), momentum=0.2
    vector_transport_method=default_vector_transport_method(M, typeof(p)),
)
```

Initialize a momentum gradient rule to `s`, where `p` and `X` are memory for interim values.
