```
vcreate([P,] A, x, scratch=false) -> y
```

yields a new instance `y` suitable for storing the result of applying mapping `A` to the argument `x`. Optional parameter `P ∈ Operations` is one of `Direct` (the default), `Adjoint`, `Inverse` and/or `InverseAdjoint` and can be used to specify how `A` is to be applied as explained in the documentation of the [`apply`](@ref) method.

Optional argument `scratch` indicates whether input argument `x` can be overwritten by the operation and thus used to store the result. This may be exploited by some mappings (which are able to operate *in-place*) to avoid allocating a new object for the result `y`.

The caller should set `scratch = true` if `x` is not needed after calling `apply`. If `scratch = true`, then it is possible that `y` be the same object as `x`; otherwise, `y` is a new object unless applying the operation yields the same contents as `y` for the result `x` (this is always true for the identity for instance). Thus, in general, it should not be assumed that the returned `y` is different from the input `x`.

The method `vcreate(::Type{P}, A, x)` should be implemented by linear mappings for any supported operations `P` and argument type for `x`. The result returned by `vcreate` should be of predictible type to ensure *type-stability*. Checking the validity (*e.g.* the size) of argument `x` in `vcreate` may be skipped because this argument will be eventually checked by the `apply!` method.

See also: [`Mapping`](@ref), [`apply`](@ref).
