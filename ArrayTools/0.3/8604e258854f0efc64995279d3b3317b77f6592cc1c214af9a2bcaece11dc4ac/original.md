`RubberIndex` is the singleron type that represents any number of indices. The constant `..` is defined as `RubberIndex()` and can be used in array indexation to left and/or right justify the other indices. For instance, assuming `A` is a `3×4×5×6` array, then all the following equalities hold:

```
A[..]           == A[:,:,:,:]
A[..,3]         == A[:,:,:,3]
A[2,..]         == A[2,:,:,:]
A[..,2:4,5]     == A[:,:,2:4,5]
A[2:3,..,1,2:4] == A[2:3,:,1,2:4]
```

As you can see, the advantage of the rubber index `..` is that it automatically expands as the number of colons needed to have the correct number of indices. The expressions are also more readable.

The rubber index may also be used for setting values. For instance:

```
A[..] .= 1         # to fill A with ones
A[..,3] = A[..,2]  # to copy A[:,:,:,2] in A[:,:,:,3]
A[..,3] .= A[..,2] # idem but faster
A[2,..] = A[3,..]  # to copy A[3,:,:,:] in A[2,:,:,:]
A[..,2:4,5] .= 7   # to set all elements in A[:,:,2:4,5] to 7
```

Leading/trailing indices may be specified as Cartesian indices (of type `CartesianIndex`).

!!! warning
    There are two known limitations:

    1. The `end` reserved word can only be used in intervals specified *before* the rubber index but not *after*. This limitation is due to the Julia parser cannot be avoided.
    2. At most 9 indices can be specified before the rubber index. This can be extended by editing the source code.


See also: [`colons`](@ref).
