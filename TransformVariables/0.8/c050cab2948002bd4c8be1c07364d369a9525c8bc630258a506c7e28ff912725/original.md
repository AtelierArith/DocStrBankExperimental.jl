```julia
CustomTransform(g, f, flatten; chunk, cfg)

```

Wrap a custom transform `y = f(transform(g, x))` in a type that calculates the log Jacobian of $∂y/∂x$ using `ForwardDiff` when necessary.

Usually, `g::TransformReals`, but when an integer is used, it amounts to the identity transformation with that dimension.

`flatten` should take the result from `f`, and return a flat vector with no redundant elements, so that $x ↦ y$ is a bijection. For example, for a covariance matrix the elements below the diagonal should be removed.

`chunk` and `cfg` can be used to configure `ForwardDiff.JacobianConfig`. `cfg` is used directly, while `chunk = ForwardDiff.Chunk{N}()` can be used to obtain a type-stable configuration.
