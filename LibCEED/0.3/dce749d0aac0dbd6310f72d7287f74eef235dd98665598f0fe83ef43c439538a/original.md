```
@interior_qf name=def
```

Creates a user-defined interior (volumetric) Q-function, and assigns it to a variable named `name`. The definition of the Q-function is given as:

```
@interior_qf user_qf=(
    ceed::CEED,
    [const1=val1, const2=val2, ...],
    [ctx::ContextType],
    (I1, :in, EvalMode, dims...),
    (I2, :in, EvalMode, dims...),
    (O1, :out, EvalMode, dims...),
    body
)
```

The definitions of form `const=val` are used for definitions which will be compile-time constants in the Q-function. For example, if `dim` is a variable set to the dimension of the problem, then `dim=dim` will make `dim` available in the body of the Q-function as a compile-time constant.

If the user wants to provide a context struct to the Q-function, that can be achieved by optionally including `ctx::ContextType`, where `ContextType` is the type of the context struct, and `ctx` is the name to which is will be bound in the body of the Q-function.

This is followed by the definition of the input and output arrays, which take the form `(arr_name, (:in|:out), EvalMode, dims...)`. Each array will be bound to a variable named `arr_name`. Input arrays should be tagged with :in, and output arrays with :out. An `EvalMode` should be specified, followed by the dimensions of the array. If the array consists of scalars (one number per Q-point) then `dims` should be omitted.

# Examples

  * Q-function to compute the "Q-data" for the mass operator, which is given by the quadrature weight times the Jacobian determinant. The mesh Jacobian (the gradient of the nodal mesh points) and the quadrature weights are given as input arrays, and the Q-data is the output array. `dim` is given as a compile-time constant, and so the array `J` is statically sized, and therefore `det(J)` will automatically dispatch to an optimized implementation for the given dimension.

```
@interior_qf build_qfunc = (
    ceed, dim=dim,
    (J, :in, EVAL_GRAD, dim, dim),
    (w, :in, EVAL_WEIGHT),
    (qdata, :out, EVAL_NONE),
    qdata[] = w*det(J)
)
```
