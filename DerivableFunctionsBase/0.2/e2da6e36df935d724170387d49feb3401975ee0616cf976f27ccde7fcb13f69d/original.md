```
GetArgLength(F::Function; max::Int=100) -> Int
```

Attempts to determine input structure of `F`, i.e. whether it accepts `Number`s or `AbstractVector`s and of what length. This is achieved by successively evaluating the function on `rand(i)` until the evaluation no longer throws errors. As a result, `GetArgLength` will be unable to determine the correct input structure if `F` errors on `rand(i)`.

!!! note
    Does NOT discriminate between `Real` and `Vector{Real}` of length one, i.e. `Real`↦`+1`. To disciminate between these two options, use `_GetArgLength()` instead.

