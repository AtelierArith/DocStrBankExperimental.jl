### parse(T::Type{Pair}, s::AbstractArray) -> ::Array{T}

Parses each element inside of of **s** into type **T**. Replaces arguments that cannot be casted with missing. **arguments**

  * T <: DataType; type to parse **s** into.
  * s <: AbstractArray; the array to be casted.

---

### example

```
example_input = ["55", "82", "hello"]
new = parse(Int64, example_input)
new
[55, 82, missing]
```
