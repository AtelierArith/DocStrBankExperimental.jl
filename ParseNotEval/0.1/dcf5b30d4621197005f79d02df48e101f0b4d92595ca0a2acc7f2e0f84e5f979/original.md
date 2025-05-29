### parse(T::Type{Array}, s::AbstractString) -> ::Array{typeof(parse(Any, **s**))}

Parses **s** into type **T**. **arguments**

  * T <: DataType; type to parse **s** into.
  * s <: AbstractString; string to be parsed into type **T**.

---

### example

```
example_input = "[5, 10, 15, 20]"
my_array::Array{Int64} = parse(Array, example_input)
[5, 10, 15, 20]
my_array::Array{Float64} = parse(Float64, my_array)
[5.0, 10.0, 15.0, 20.0]
```
