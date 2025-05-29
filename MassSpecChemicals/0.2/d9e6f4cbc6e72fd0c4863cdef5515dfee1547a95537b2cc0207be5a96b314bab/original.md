```
parse_adduct(::AbstractString) -> AbstractAdduct
```

Parse string into `AbstractAdduct`. This function searches string in `ELEMENTS[:NAME]` first, then destructs the input string and constructs a `PosAdduct` or `NegAdduct`.
