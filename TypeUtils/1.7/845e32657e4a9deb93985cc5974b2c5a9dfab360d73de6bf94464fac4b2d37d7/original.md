```
convert_eltype(T, A) -> B
```

converts the element type of object/type `A` to type `T`. The returned object/type is similar to `A` except maybe for the element type. For example, if `A` is a range, then `B` is also a range. If `T` is the element type of `A`, then `A` may be returned.

Consider using [`as_eltype(T, A)`](@ref as_eltype) to build an object that lazily performs the conversion.

To simplify extending `convert_eltype` for objects `A` of given type, the default behavior is:

```
convert_eltype(T, A) = as(convert_eltype(T, typeof(A)), A)
```

so that it may be sufficient to extend `convert_eltype` for the type of the objects.
