FunctionOperator is an operator that maps from a multidimensional space to another multidimensional space. The mapping is defined by a function (`forw`), and optionally the reverse mapping can also be defined (`backw`). The input the mapping must be subtype of AbstractArray.

The following constructors are available:

  * Positional constructor #1: `FunctionOperator{eltype}(forw, inDims, outDims)`
  * Positional constructor #2: `FunctionOperator{eltype}(forw, backw, inDims, outDims)`
  * Positional constructor #3: `FunctionOperator{eltype}(name, forw, inDims, outDims)`
  * Positional constructor #4: `FunctionOperator{eltype}(name, forw, backw, inDims, outDims)`
  * Keyword constructor: `FunctionOperator{eltype}(;kwargs...)`

where `eltype` is the type enforced on elements of input array.

Arguments

  * `name::String` (Optional but strongly recommended) The operator is referenced later in error messages by this string. **Warning!** It is also used to check equality of (composite) FunctionOperators. Default value: `OpX` where X is a number incremented in each constructor-call.
  * `forw::Function` Function defining the mapping. Must accept one or two arguments. In case of two arguments, the first argument is a preallocated buffer to write the result into (to speed up code by avoiding repeated allocations). In case of both one and two arguments, the return value must be the result of the mapping.
  * `backw::Function` (Optional) Same as backw, but defines the backward mapping
  * `inDims::Tuple{Vararg{Int}}` Size of input array
  * `outDims::Tuple{Vararg{Int}}` Size of output array
