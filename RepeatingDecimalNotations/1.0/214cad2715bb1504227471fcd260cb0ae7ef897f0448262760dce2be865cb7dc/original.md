```
RepeatingDecimal
```

Intermediate struct to represent a repeating decimal number.

# Examples

```julia-repl
julia> RepeatingDecimal(false, 12743, 857142, 2, 6)
       2|--|------|6
    -127.43(857142)
----------- --------------
Finite part Repeating part

julia> RepeatingDecimal(1//17)
         0||----------------|16
        +0.(0588235294117647)
----------- -------------------
Finite part Repeating part
```
