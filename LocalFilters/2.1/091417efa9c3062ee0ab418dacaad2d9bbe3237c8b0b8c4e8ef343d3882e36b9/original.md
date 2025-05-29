```
localfilter!(dst, A, B, initial, update::Function, final::Function=identity;
             order=FORWARD_FILTER) -> dst
```

overwrites the destination `dst` with the result of a local filter applied to the source `A`, on a relative neighborhood defined by `B`, and implemented by `initial`, `update`, and `final`. The `initial` argument may be a function or not. The purpose of these latter arguments is explained by the following pseudo-codes implementing the local filtering. Keyword `order` specifies the filter direction, `FORWARD_FILTER` by default.

If `order = FORWARD_FILTER`:

```
@inbounds for i ∈ indices(dst)
    v = initial isa Function ? initial(A[i]) : initial
    for j ∈ indices(A) ∩ (indices(B) + i)
        v = update(v, A[j], B[j-i])
    end
    dst[i] = final(v)
end
```

else if `order = REVERSE_FILTER`:

```
@inbounds for i ∈ indices(dst)
    v = initial isa Function ? initial(A[i]) : initial
    for j ∈ indices(A) ∩ (i - indices(B))
        v = update(v, A[j], B[i-j])
    end
    dst[i] = final(v)
end
```

where `indices(A)` denotes the range of indices of any array `A` while `indices(B) + i` and `i - indices(B)` respectively denote the set of indices `j` such that `j - i ∈ indices(B)` and `i - j ∈ indices(B)`. In other words, `j ∈ indices(A) ∩ (i - indices(B))` means all indices `j` such that `j ∈ indices(A)` and `i - j ∈ indices(B)` so that `A[j]` and `B[i-j]` are in-bounds.

If `initial` is a function, the initial value of the state variable `v` in the above pseudo-codes is given by `v = initial(A[i])` with `i` the current index in `dst`. Hence, in that case, the destination array `dst` and the source array `src` must have the same axes.

For example, implementing a local minimum filter (that is, an *erosion*), is as simple as:

```
localfilter!(dst, A, B, typemax(eltype(A)),
             (v,a,b) -> ifelse(b, min(v,a), v))
```

As another example, implementing a convolution by `B` writes:

```
T = promote_type(eltype(A), eltype(B))
localfilter!(dst, A, B, zero(T), (v,a,b) -> v + a*b)
```
