### parse(T::Type{Date}, s::AbstractString) -> ::Date

Parses a date, with appropriate formatting, from string to date. Requires '-' separators be used. **arguments**

  * T <: DataType; type to parse **s** into.
  * s <: AbstractString; string to be parsed into type **T**.

---

### example

```
example_input::String = "1999-11-23"
symb::Date = parse(Date, example_input)
typeof(myint) == Date
true
```
