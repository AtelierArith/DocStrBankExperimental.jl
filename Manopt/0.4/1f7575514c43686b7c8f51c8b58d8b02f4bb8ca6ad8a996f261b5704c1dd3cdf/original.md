```
AverageGradient <: DirectionUpdateRule
```

Add an average of gradients to a gradient processor. A set of previous directions (from the inner processor) and the last iterate are stored, average is taken after vector transporting them to the current iterates tangent space.

# Fields

  * `gradients`:               the last `n` gradient/direction updates
  * `last_iterate`:            last iterate (needed to transport the gradients)
  * `direction`:               internal [`DirectionUpdateRule`](@ref) to determine directions to apply the averaging to
  * `vector_transport_method`: vector transport method to use

# Constructors

```
AverageGradient(
    M::AbstractManifold,
    p::P=rand(M);
    n::Int=10
    s::DirectionUpdateRule=IdentityUpdateRule();
    gradients = fill(zero_vector(p.M, o.x),n),
    last_iterate = deepcopy(x0),
    vector_transport_method = default_vector_transport_method(M, typeof(p))
)
```

Add average to a gradient problem, where

  * `n`:                       determines the size of averaging
  * `s`:                       is the internal [`DirectionUpdateRule`](@ref) to determine the gradients to store
  * `gradients`:               can be pre-filled with some history
  * `last_iterate`:            stores the last iterate
  * `vector_transport_method`: determines how to transport all gradients to the current iterates tangent space before averaging
