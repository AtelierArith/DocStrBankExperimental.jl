### parse(s::AbstractString) -> ::Any

Binded call for parse(::DataType{Any}, ::AbstractString). Parses string into     assumed type. **arguments**

  * T <: DataType; type to parse **s** into.
  * s <: AbstractString; string to be parsed into type **T**.

---

### example

```
parse("55")
Int64(55)
```
