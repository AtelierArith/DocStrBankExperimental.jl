```
SoftDot
```

The SoftDot node can be used as a substitute for the dot product operator delta node (the outgoing variable is the dot product of two others).  It softens the delta constraint by adding a Gaussian noise as follows:

```
y ~ N(dot(θ, x), γ^(-1))
```

Interfaces:

1. y - result of the "soft" dot product,
2. θ - first variable to be multiplied,
3. x - second variable to be multiplied,
4. γ - precision of the Gaussian noise.

The advantage of using SoftDot is that it offers tractable and optimized closed-form variational messages  for both Belief Propagation and Variational Message Passing.

See also: [`softdot`](@ref)
