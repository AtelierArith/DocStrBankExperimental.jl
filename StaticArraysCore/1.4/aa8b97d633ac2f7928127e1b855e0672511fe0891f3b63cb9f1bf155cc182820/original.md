```
abstract FieldArray{N, T, D} <: StaticArray{N, T, D}
```

Inheriting from this type will make it easy to create your own rank-D tensor types. A `FieldArray` will automatically define `getindex` and `setindex!` appropriately. An immutable `FieldArray` will be as performant as an `SArray` of similar length and element type, while a mutable `FieldArray` will behave similarly to an `MArray`.

Note that you must define the fields of any `FieldArray` subtype in column major order. If you want to use an alternative ordering you will need to pay special attention in providing your own definitions of `getindex`, `setindex!` and tuple conversion.

If you define a `FieldArray` which is parametric on the element type you should consider defining `similar_type` as in the `FieldVector` example.

# Example

```
struct Stiffness <: FieldArray{Tuple{2,2,2,2}, Float64, 4}
    xxxx::Float64
    yxxx::Float64
    xyxx::Float64
    yyxx::Float64
    xxyx::Float64
    yxyx::Float64
    xyyx::Float64
    yyyx::Float64
    xxxy::Float64
    yxxy::Float64
    xyxy::Float64
    yyxy::Float64
    xxyy::Float64
    yxyy::Float64
    xyyy::Float64
    yyyy::Float64
end
```
