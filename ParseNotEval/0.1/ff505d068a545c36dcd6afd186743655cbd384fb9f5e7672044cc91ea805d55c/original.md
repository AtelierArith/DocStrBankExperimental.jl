### parse(T::Type{Any}, s::AbstractString) -> ::Any

Trys to guess the type of a string implicitly. For a more explicit assumption of type, try passing the type as the first argument. **arguments**

  * T <: DataType; type to parse **s** into.
  * s <: AbstractString; string to be parsed into type **T**.

---

### example

```
example_input = "[5, 10, 15, 20]"
my_array::Array{Int64} = parse(Array, example_input)
[5, 10, 15, 20]

example_input = "5"
myint::Int64 = parse(Any, example_input)
```
