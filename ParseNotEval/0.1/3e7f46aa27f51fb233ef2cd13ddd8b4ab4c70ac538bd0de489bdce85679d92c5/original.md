### parse(T::Type{DateTime}, s::AbstractString) -> ::DateTime

Parses a date with time, with appropriate formatting, from string to date. Requires '-' and ':' separators be used. **arguments**

  * T <: DataType; type to parse **s** into.
  * s <: AbstractString; string to be parsed into type **T**.

---

### example

```
example_input::String = "1999-11-23:8000"
symb::DateTime = parse(DateTime, example_input)
typeof(myint) == DateTime
true
```
