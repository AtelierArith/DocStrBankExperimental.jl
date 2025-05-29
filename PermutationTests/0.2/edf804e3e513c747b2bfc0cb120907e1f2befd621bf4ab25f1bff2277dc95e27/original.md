```julia
function studentTest1S!(y::UniData; <same args and kwargs as `studentTest1S`>)
```

As [`studentTest1S`](@ref), but `y` is overwritten in the case of approximate (random permutations) tests.

**Alias:** `tTest1S!`

**Multiple Comparison version:** [`studentMcTest1S!`](@ref)
