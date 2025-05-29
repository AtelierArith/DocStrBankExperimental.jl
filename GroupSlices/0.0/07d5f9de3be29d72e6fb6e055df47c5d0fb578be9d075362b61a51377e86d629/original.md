```
groupslices(A; dims) = groupslices(A, dims)
```

Returns a vector of integers where each integer element of the returned vector is a group number corresponding to the unique slices along dimension `dims` as returned from `unique(A; dims=d)`, where `A` can be a multidimensional array. The default is `dims = 1`.

Example usage:

If `C = unique(A; dims=dims)`, `ic = groupslices(A, dims)`, and `ndims(A) == ndims(C) == 3`, then:

```
if dims == 1
   all(A .== C[ic,:,:])
elseif dims == 2
   all(A .== C[:,ic,:])
elseif dims == 3
   all(A .== C[:,:,ic])
end
```
