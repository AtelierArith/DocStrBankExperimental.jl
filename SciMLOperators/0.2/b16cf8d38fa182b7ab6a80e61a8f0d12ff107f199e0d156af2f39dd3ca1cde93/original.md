```julia
FunctionOperator(op, input; ...)
FunctionOperator(
    op,
    input,
    output;
    op_adjoint,
    op_inverse,
    op_adjoint_inverse,
    p,
    t,
    accepted_kwargs,
    T,
    isinplace,
    outofplace,
    has_mul5,
    isconstant,
    islinear,
    batch,
    ifcache,
    cache,
    opnorm,
    issymmetric,
    ishermitian,
    isposdef
)

```

Wrap callable object `op` within an `AbstractSciMLOperator`. `op` is assumed to have signature

```
op(u, p, t; <accepted_kwargs>) -> v
```

or

```
op(v, u, p, t; <accepted_kwargs>) -> [modifies v]
```

and optionally

```
op(v, u, p, t, α, β; <accepted_kwargs>) -> [modifies v]
```

where `u`, `v` are `AbstractVecOrMat`s, `p` is a parameter object, and `t`, `α`, `β` are scalars. The first signautre corresponds to applying the operator with `Base.*`, and the latter two correspond to the three-argument, and the five-argument `mul!` respectively.

`input` and `output` prototype `AbstractVecOrMat`s are required for determining operator traits such as `eltype`, `size`, and for preallocating cache. If `output` array is not provided, the output is assumed to be of the same type and share as the input.

# Keyword Arguments

Keyword arguments are used to pass in the adjoint evaluation function, `op_adjoint`, the inverse function, `op_inverse`, and the adjoint-inverse function `adjoint_inverse`. All are assumed to have the same calling signature and below traits.

## Traits

Keyword arguments are used to set operator traits, which are assumed to be uniform across `op`, `op_adjoint`, `op_inverse`, `op_adjoint_inverse`.

  * `p` - Prototype of parameter struct passed to the operator during evaluation, i.e. `L(u, p, t)`. `p` is set to `nothing` if no value is provided.
  * `t` - Protype of scalar time variable passed to the operator during evaluation. `t` is set to `zero(T)` if no value is provided.
  * `accepted_kwargs` - `Tuple` of `Symbol`s corresponding to the keyword arguments accepted by `op*`, and `update_coefficients[!]`. For example, if `op` accepts kwarg `scale`, as in `op(u, p, t; scale)`, then `accepted_kwargs = (:scale,)`.
  * `T` - `eltype` of the operator. If no value is provided, the constructor inferrs the value from types of `input`, and `output`
  * `isinplace` - `true` if the operator can be used is a mutating way with in-place allocations. This trait is inferred if no value is provided.
  * `outofplace` - `true` if the operator can be used is a non-mutating way with in-place allocations. This trait is inferred if no value is provided.
  * `has_mul5` - `true` if the operator provides a five-argument `mul!` via the signature `op(v, u, p, t, α, β; <accepted_kwargs>)`. This trait is inferred if no value is provided.
  * `isconstant` - `true` if the operator is constant, and doesn't need to be updated via `update_coefficients[!]` during operator evaluation.
  * `islinear` - `true` if the operator is linear. Defaults to `false`.
  * `batch` - Boolean indicating if the input/output arrays comprise of batched vectors. If `true`, the last dimension of input/output arrays is considered to be the batch dimension and is not involved in size computation. For example, let `size(output), size(input) = (M, K), (N, K)`. If `batch = true`, then the second dimension is assumed to be the batch dimension, and the `size(F::FunctionOperator) = (M, N)`. If `batch = false`, then `size(F::FunctionOperator) = (M * K, M * K)`.
  * `ifcache` - Allocate cache arrays in constructor. Defaults to `true`. Cache can be generated afterwards by calling `cache_operator(L, input, output)`
  * `cache` - Pregenerated cache arrays for in-place evaluations. Expected to be of type and shape `(similar(input), similar(output),)`. The constructor generates cache if no values are provided. Cache generation by the constructor can be disabled by setting the kwarg `ifcache = false`.
  * `opnorm` - The norm of `op`. Can be a `Number`, or function `opnorm(p::Integer)`. Defaults to `nothing`.
  * `issymmetric` - `true` if the operator is linear and symmetric. Defaults to `false`.
  * `ishermitian` - `true` if the operator is linear and hermitian. Defaults to `false`.
  * `isposdef` - `true` if the operator is linear and positive-definite. Defaults to `false`.
