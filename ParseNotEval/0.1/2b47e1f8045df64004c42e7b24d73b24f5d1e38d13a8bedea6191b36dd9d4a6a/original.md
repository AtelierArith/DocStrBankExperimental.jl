### parse(T::Type{Dict}, s::AbstractString) -> ::Dict

Parses a dict. Can inclkude any of the following examples of input:

  * JSON data; e.g. "{A:5, x:6}"
  * Dict data; e.g. "A => [5, 10, 15, 20], B => [5, 10, 15, 20]"

**arguments**

  * T <: DataType; type to parse **s** into.
  * s <: AbstractString; string to be parsed into type **T**.

---

### example

```
example_input::String = "{x => [5, 10, 15], y = [5, 8, 7]}"
my_dct::Dict = parse(Dict, example_input)

example_input::String = "{x : [5, 10, 15], y : [5, 8, 7]}"
my_dct::Dict = parse(Dict, example_input)

typeof(myint) == Dict
true
```
