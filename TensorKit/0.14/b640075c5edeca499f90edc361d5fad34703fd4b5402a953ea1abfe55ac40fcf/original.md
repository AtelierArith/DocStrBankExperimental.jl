```
abstract type ElementarySpace <: VectorSpace end
```

Elementary finite-dimensional vector space over a field that can be used as the index space corresponding to the indices of a tensor. ElementarySpace is a supertype for all vector spaces (objects) that can be associated with the individual indices of a tensor, as hinted to by its alias IndexSpace.

Every elementary vector space should respond to the methods [`conj`](@ref) and [`dual`](@ref), returning the complex conjugate space and the dual space respectively. The complex conjugate of the dual space is obtained as `dual(conj(V)) === conj(dual(V))`. These different spaces should be of the same type, so that a tensor can be defined as an element of a homogeneous tensor product of these spaces.
