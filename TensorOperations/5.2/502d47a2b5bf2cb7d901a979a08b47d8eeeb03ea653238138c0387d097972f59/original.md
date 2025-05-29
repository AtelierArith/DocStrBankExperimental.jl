```
@tensor(tensor_expr; kwargs...)
@tensor [kw_expr...] tensor_expr
```

Specify one or more tensor operations using Einstein's index notation. Indices can be chosen to be arbitrary Julia variable names, or integers. When contracting several tensors together, this will be evaluated as pairwise contractions in left to right order, unless the so-called NCON style is used (positive integers for contracted indices and negative indices for open indices).

Additional keyword arguments may be passed to control the behavior of the parser:

  * `order`:    A list of contraction indices of the form `order=(...,)` which specify the order in which they will be contracted.
  * `opt`:   Contraction order optimization, similar to [`@tensoropt`](@ref). Can be either a boolean or an `OptExpr`.
  * `contractcheck`:   Boolean flag to enable runtime check for contractibility of indices with clearer error messages.
  * `costcheck`:   Can be either `:warn` or `:cache` and adds runtime checks to compare the compile-time contraction order to the optimal order computed for the actual run time tensor costs.   If `costcheck == :warn`, warnings are printed for every sub-optimal contraction that is encountered.   If `costcheck == :cache`, only the most costly run of a particular sub-optimal contraction will be cached in `TensorOperations.costcache`.   In both cases, a suggestion for the `order` keyword argument is computed to switch to the optimal contraction order.
  * `backend`:    Inserts an implementation backend as a final argument in the different tensor operation calls in the generated code.
  * `allocator`:   Inserts an allocation strategy as a final argument in the tensor allocation calls in the generated code.
