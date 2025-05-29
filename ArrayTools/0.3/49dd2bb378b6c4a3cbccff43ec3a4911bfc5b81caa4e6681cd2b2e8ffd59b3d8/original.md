Assuming `A` and `B` are arrays with `N` dimensions:

```
common_indices(A, B) -> inds
```

yields the set of all the indices that are valid for both `A` and `B`. The result is similar to `axes(A)` or `axes(B)`, that is an `N`-tuple of integer valued unit ranges.

An offset `k` with a sign may be specified:

```
common_indices(A, B, ±, k)
```

to obtain the set of all indices `i` such that `A[i]` and `B[i ± k]` are valid and where here and above `±` is either `+` or `-`. Offset `k` can be a tuple of integers or a Cartesian index.

Arguments `A` and `B` may be both tuples of indices or index ranges or both scalar or index range which specify the size or the axes of the arrays to be indexed. This is used in the following example, where we want to do `A[i] = B[i]*C[i + k]` given the offset `k` and for all valid indices `i`:

```
I = common_indices(same_axes(A, B), axes(C), +, k)
@inbounds @simd for i in CartesianIndices(I)
   A[i] = B[i]*C[i + k]
end
```

Note that `same_axes(A,B)` is called to get the axes of `A` and `B` while asserting that they are the same, as a result no bound checking is necessary and the loop can be optimized for vectorization.
