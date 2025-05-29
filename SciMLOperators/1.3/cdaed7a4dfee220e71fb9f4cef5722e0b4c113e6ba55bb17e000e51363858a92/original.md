```julia
FunctionOperator(op, input; ...)
FunctionOperator(
    op,
    input,
    output;
    op_adjoint,
    op_inverse,
    op_adjoint_inverse,
    u,
    p,
    t,
    accepted_kwargs,
    T,
    isinplace,
    outofplace,
    has_mul5,
    isconstant,
    islinear,
    isconvertible,
    batch,
    ifcache,
    cache,
    opnorm,
    issymmetric,
    ishermitian,
    isposdef,
    kwargs...
)

```

Wrap callable object `op` within an `AbstractSciMLOperator`. 

## Mathematical Description

```julia
L = FunctionOperator(op, v, w; kwargs...)
```

where $w = L(u,p,t)*v$ is done matrix-free given the function definition $w = op(v,u,p,t)$.

## Arguments

`op` is assumed to have signature

```
op(v, u, p, t; <accepted_kwargs>) -> w
```

or

```
op(w, v, u, p, t; <accepted_kwargs>) -> [modifies w]
```

and optionally

```
op(w, v, u, p, t, α, β; <accepted_kwargs>) -> [modifies w]
```

where `u`, `v`, `w` are `AbstractArray`s, `p` is a parameter object, and `t`, `α`, `β` are scalars. The first signature corresponds to applying the operator with `Base.*`, and the latter two correspond to the three-argument, and the five-argument `mul!` respectively.

`input` and `output` prototype `AbstractArray`s are required for determining operator traits such as `eltype`, `size`, and for preallocating cache. If `output` array is not provided, the output is assumed to be of the same type and share as the input.

## Keyword Arguments

Keyword arguments are used to pass in the adjoint evaluation function, `op_adjoint`, the inverse function, `op_inverse`, and the adjoint-inverse function `adjoint_inverse`. All are assumed to have the same calling signature and below traits.

## Traits

Keyword arguments are used to set operator traits, which are assumed to be uniform across `op`, `op_adjoint`, `op_inverse`, `op_adjoint_inverse`.

  * `u` - Prototype of the state struct passed to the operator during evaluation, i.e. `L(u, p, t)`. `u` is set to `nothing` if no value is provided.
  * `p` - Prototype of parameter struct passed to the operator during evaluation, i.e. `L(u, p, t)`. `p` is set to `nothing` if no value is provided.
  * `t` - Protype of scalar time variable passed to the operator during evaluation. `t` is set to `zero(T)` if no value is provided.
  * `accepted_kwargs` - `Tuple` of `Symbol`s corresponding to the keyword arguments accepted by `op*`, and `update_coefficients[!]`. For example, if `op` accepts kwarg `scale`, as in `op(u, p, t; scale)`, then `accepted_kwargs = (:scale,)`.
  * `T` - `eltype` of the operator. If no value is provided, the constructor inferrs the value from types of `input`, and `output`
  * `isinplace` - `true` if the operator can be used is a mutating way with in-place allocations. This trait is inferred if no value is provided.
  * `outofplace` - `true` if the operator can be used is a non-mutating way with in-place allocations. This trait is inferred if no value is provided.
  * `has_mul5` - `true` if the operator provides a five-argument `mul!` via the signature `op(v, u, p, t, α, β; <accepted_kwargs>)`. This trait is inferred if no value is provided.
  * `isconstant` - `true` if the operator is constant, and doesn't need to be updated via `update_coefficients[!]` during operator evaluation. Defaults to false.
  * `islinear` - `true` if the operator is linear. Defaults to `false`.
  * `isconvertible` - `true` a cheap `convert(AbstractMatrix, L.op)` method is available. Defaults to `false`.
  * `batch` - Boolean indicating if the input/output arrays comprise of batched column-vectors stacked in a matrix. If `true`, the input/output arrays must be `AbstractVecOrMat`s, and the length of the  second dimension (the batch dimension) must be the same. The batch dimension is not involved in size computation. For example, with `batch = true`, and `size(output), size(input) = (M, K), (N, K)`, the `FunctionOperator` size is set to `(M, N)`. If `batch = false`, which is the default, the `input`/`output` arrays may of any size so long as `ndims(input) == ndims(output)`, and the `size` of `FunctionOperator` is set to `(length(input), length(output))`.
  * `ifcache` - Allocate cache arrays in constructor. Defaults to `true`. Cache can be generated afterwards by calling `cache_operator(L, input, output)`
  * `cache` - Pregenerated cache arrays for in-place evaluations. Expected to be of type and shape `(similar(input), similar(output),)`. The constructor generates cache if no values are provided. Cache generation by the constructor can be disabled by setting the kwarg `ifcache = false`.
  * `opnorm` - The norm of `op`. Can be a `Number`, or function `opnorm(p::Integer)`. Defaults to `nothing`.
  * `issymmetric` - `true` if the operator is linear and symmetric. Defaults to `false`.
  * `ishermitian` - `true` if the operator is linear and hermitian. Defaults to `false`.
  * `isposdef` - `true` if the operator is linear and positive-definite. Defaults to `false`.
  * `kwargs` - Keyword arguments for cache initialization. If `accepted_kwargs` is provided, the corresponding keyword arguments must be passed.
