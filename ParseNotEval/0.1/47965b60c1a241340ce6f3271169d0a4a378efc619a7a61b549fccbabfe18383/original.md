### parse(T::Type{Pair}, s::AbstractString) -> ::Pair

Parses a string **s** into type **T**. **arguments**

  * T <: DataType; type to parse **s** into.
  * s <: AbstractString; string to be parsed into type **T**.

---

### example

```
example_input::String = "x => 5"
symb::Pair = parse(Pair, example_input)
typeof(myint) == Pair
true
```
