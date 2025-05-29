```
    LabelNumeral{T<:Integer}
```

Wrapper around an `Integer` type that provides the following caabilities:

1. Prefix - like A-1, A-2 etc...
2. Lower case or upper case conversions
3. show and print options.
4. Mathematical operators like `+, -, <=, ==, >, isless, max and min`

The wrapped `struct` should implement the following methods:

```
1. T(::String)
2. T(::Int)
3. Base.hash(::T)
4. Base.convert{S <: Integer}(::Type{S}, num::T)  <-- to covert to standard numeral types
```
