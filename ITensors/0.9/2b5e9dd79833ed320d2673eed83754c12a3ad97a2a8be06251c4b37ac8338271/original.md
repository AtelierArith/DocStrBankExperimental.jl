```
nullspace(T::ITensor, left_inds...; tags="n", atol=1E-12, kwargs...)
```

Viewing the ITensor `T` as a matrix with the provided `left_inds` viewed as the row space and remaining indices viewed as the right indices or column space, the `nullspace` function computes the right null space. That is, it will return a tensor `N` acting on the right indices of `T` such that `T*N` is zero. The returned tensor `N` will also have a new index with the label "n" which indexes through the 'vectors' in the null space.

For example, if `T` has the indices `i,j,k`, calling `N = nullspace(T,i,k)` returns `N` with index `j` such that

```
       ___       ___
  i --|   |     |   |
      | T |--j--| N |--n  ≈ 0
  k --|   |     |   |
       ---       ---
```

The index `n` can be obtained by calling `n = uniqueindex(N,T)`

Note that the implementation of this function is subject to change in the future, in which case the precise `atol` value that gives a certain null space size may change in future versions of ITensor.

Keyword arguments:

  * `atol::Float64=1E-12` - singular values of T†*T below this value define the null space
  * `tags::String="n"` - choose the tags of the index selecting elements of the null space
