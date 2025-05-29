### parse(T::Type{Symbol}, s::AbstractString) -> ::Symbol

Parses a symbol, without the colon. It is really a simple binded call to the constructor Symbol(::AbstractString). **arguments**

  * T <: DataType; type to parse **s** into.
  * s <: AbstractString; string to be parsed into type **T**.

---

### example

```
example_input::String = "hello"
symb::Symbol = parse(Symbol, example_input)

:hello

typeof(myint) == Symbol
true
```
