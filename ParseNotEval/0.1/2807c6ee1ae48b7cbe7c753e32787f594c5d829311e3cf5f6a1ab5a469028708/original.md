### parse(T::Type{String}, s::AbstractString) -> ::String

Although parsing a string into a string is not necessary, the reason why the binding exists is so that if dims are parsed by type, they can still have a     normal return whenever they are strings. **arguments**

  * T <: DataType; type to parse **s** into.
  * s <: AbstractString; string to be parsed into type **T**.

---

### example

```
example_input = "5"
myint::Int64 = parse(String, example_input)
typeof(myint) == String
true
```
