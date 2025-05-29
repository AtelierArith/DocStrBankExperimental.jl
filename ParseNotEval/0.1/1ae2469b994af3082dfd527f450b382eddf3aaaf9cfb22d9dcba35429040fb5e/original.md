### parse(T::Type{Pair}, s::Pair) -> ::Pair{Symbol, T}

Parses the pair value **s[2]** into type **T**. **arguments**

  * T <: DataType; type to parse **s** into.
  * s <: AbstractArray; the array to be casted.

---

### example

```
example_input::Pair = :A => "5"
new::Pair = parse(Int64, example_input)
new
:A => 5
```
