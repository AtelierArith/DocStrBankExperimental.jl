```
abstract FieldMatrix{N1, N2, T} <: FieldArray{Tuple{N1, N2}, 2}
```

Inheriting from this type will make it easy to create your own rank-two tensor types. A `FieldMatrix` will automatically define `getindex` and `setindex!` appropriately. An immutable `FieldMatrix` will be as performant as an `SMatrix` of similar length and element type, while a mutable `FieldMatrix` will behave similarly to an `MMatrix`.

Note that the fields of any subtype of `FieldMatrix` must be defined in column major order unless you are willing to implement your own `getindex`.

If you define a `FieldMatrix` which is parametric on the element type you should consider defining `similar_type` as in the `FieldVector` example.

# Example

```
struct Stress <: FieldMatrix{3, 3, Float64}
    xx::Float64
    yx::Float64
    zx::Float64
    xy::Float64
    yy::Float64
    zy::Float64
    xz::Float64
    yz::Float64
    zz::Float64
end
```

Note that the fields of any subtype of `FieldMatrix` must be defined in column major order.  This means that formatting of constructors for literal `FieldMatrix` can be confusing. For example

```
sigma = Stress(1.0, 2.0, 3.0,
               4.0, 5.0, 6.0,
               7.0, 8.0, 9.0)

3×3 Stress:
 1.0  4.0  7.0
 2.0  5.0  8.0
 3.0  6.0  9.0
```

will give you the transpose of what the multi-argument formatting suggests. For clarity, you may consider using the alternative

```
sigma = Stress(SA[1.0 2.0 3.0;
                  4.0 5.0 6.0;
                  7.0 8.0 9.0])
```
