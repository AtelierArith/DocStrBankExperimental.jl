```julia
function correlationTest!(<same args and kwargs as `correlationTest`>)
```

As [`correlationTest`](@ref), but `x` is overwritten if neither `standardized` nor `centered` is true.

*Aliases:* `rTest!`, [`trendTest!`](@ref) 

*Multiple comparisons version:* [correlationMcTest!](@ref)
