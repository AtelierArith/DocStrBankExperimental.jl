```
ScientificNotation <: RepeatingDecimalNotation
```

A type to represent a repeating decial with scientific notation like "0.1r6".

```jldoctest
julia> rd"123.45r678"
4111111//33300

julia> no = ScientificNotation()
ScientificNotation()

julia> stringify(no, 1//11)
"0.r09"

julia> rationalify(no, "123.45r678")
4111111//33300

julia> rd"1.2345r678e2"  # Exponent term is supported.
4111111//33300
```
