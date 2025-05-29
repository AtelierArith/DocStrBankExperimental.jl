Operation represening function call on tape. Typically, calls are constructed using [`mkcall`](@ref) function.

Important fields of a Call{T}:

  * `fn::T` - function or object to be called
  * `args::Vector` - vector of variables or values used as arguments
  * `val::Any` - the result of the function call
