```
copy_array(array::AbstractArray)::AbstractArray
```

Create a mutable copy of an array. This differs from `Base.copy` in the following:

  * Copying a read-only array is a mutable array. In contrast, both `Base.copy` and `Base.deepcopy` of a read-only array will return a read-only array, which is technically correct, but is rather pointless for `Base.copy`.
  * Copying will preserve the layout of the data; for example, copying a `Transpose` array is still a `Transpose` array. In contrast, while `Base.deepcopy` will preserve the layout, `Base.copy` will silently [`relayout!`](@ref) the matrix, which is both expensive and confusing.
  * Copying a sparse vector or matrix gives the same type of sparse array or matrix. Copying anything else gives a simple dense array regardless of the original type. This is done because a `deepcopy` of `PyArray` will still share the underlying buffer. Sigh.
  * Copying a vector of anything derived from `AbstractString` returns a vector of `AbstractString`.
