```julia
struct ParsingError <: CTBase.CTException
```

Exception thrown for syntax error during abstract parsing.

**Fields**

  * `var::String`
