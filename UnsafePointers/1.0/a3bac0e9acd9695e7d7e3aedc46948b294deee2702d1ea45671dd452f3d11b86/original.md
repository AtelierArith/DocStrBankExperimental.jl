```
UnsafePtr{T}(r)
```

A pointer to the contents of `r` which may be a `Ptr`, `Ref`, `Array`, `String` or anything with a `pointer(r)` method.

`T` specifies the element type and is optional.

It has convenient (but unsafe) semantics:

  * `p[]` dereferences the element, and can be assigned to.
  * `p[i]` dereferences the `i`th element, assuming the pointer points to an array.
  * `p.name` is an `UnsafePtr` to the `name` field of `p[]`. For tuples, `p._n` refers to the `n`th field.
  * `p+i` is an `UnsafePtr` to the `i`th next element. `(p+i-1)[]` and `p[i]` are equivalent.
  * `p-q` is the number of elements between `p` and `q`, so that `p === q+(p-q)`.
  * Iteration yields `p[1]`, `p[2]`, ... forever.
  * `Array(p, dims...)` is an array view of contiguous data pointed to by `p` (equivalent to `unsafe_wrap(Array, pointer(p), dims)`).
  * `p[idxs]`/`view(p, idxs)` is an array/view of the `i`th element for each `i ∈ idxs`.
  * `String(p, [length])` converts `p` to a string (equivalent to `unsafe_string(pointer(p), length)`).

The first four operations have these C equivalents: `*p`, `p[i-1]`, `&(p->name)` and `p+i`.

If the result of dereferencing is pointer-like then an `UnsafePtr` is returned instead (see [`doautowrap`](@ref)). Use `p[!,i]` or `unsafe_load(p,i)` to get the original value.

# Safety

It is the caller's responsibility to ensure that the pointer remains valid, e.g. by ensuring that `r` is not garbage collected.

You will likely crash Julia if you assign to a non-bitstype value.

# Example

Here we access and modify the individual fields of a (mutable) reference to a (immutable) named tuple.

```julia
r = Ref((a=1, b=(2, 3)))
@show r[]            # (a = 1, b = (2, 3))
p = UnsafePtr(r)
p.a[] = 99
p.b._2[] *= 10
@show r[]            # (a = 99, b = (2, 30))
@show Array(p.a, 3)  # [99, 2, 30]
```
