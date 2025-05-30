GroupedArray{T,N} <: AbstractArray{T,N} N-dimensional dense array with elements of type T, where T <: Union{Int, Missing}

GroupedArray has a field ngroups which satisfies the following contract:

  * Right after construction, the set of non missing elements in the GroupedArray is equal to 1:ngroups.
  * Afterwards (ie, after using `setindex!`), non missing elements always remain between 1 and ngroups.
