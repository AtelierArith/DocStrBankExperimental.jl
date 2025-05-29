```
apply([P=Direct,] A, x, scratch=false) -> y
```

yields the result `y` of applying mapping `A` to the argument `x`. Optional parameter `P` can be used to specify how `A` is to be applied:

  * `Direct` (the default) to apply `A` and yield `y = A⋅x`;
  * `Adjoint` to apply the adjoint of `A` and yield `y = A'⋅x`;
  * `Inverse` to apply the inverse of `A` and yield `y = A\x`;
  * `InverseAdjoint` or `AdjointInverse` to apply the inverse of `A'` and yield `y = A'\x`.

Not all operations may be implemented by the different types of mappings and `Adjoint` and `InverseAdjoint` may only be applicable for linear mappings.

Optional argument `scratch` indicates whether input argument `x` can be overwritten by the operation. This may be exploited to avoid allocating temporary workspace(s). The caller should set `scratch = true` if `x` is not needed after calling `apply`. If `scratch = true`, then it is possible that `y` be the same object as `x`; otherwise, `y` is a new object unless applying the operation yields the same contents as `y` for the result `x` (this is always true for the identity for instance). Thus, in general, it should not be assumed that the result of applying a mapping is different from the input.

Julia methods are provided so that `apply(A', x)` automatically calls `apply(Adjoint, A, x)` so the shorter syntax may be used without impacting performances.

See also: [`Mapping`](@ref), [`apply!`](@ref), [`vcreate`](@ref).
