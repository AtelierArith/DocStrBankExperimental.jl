```
struct BooleanAlgebra <: AbstractAlgebra{Bool} end
```

A [Boolean algebra](https://en.wikipedia.org/wiki/Boolean_algebra), defined on the values TOP (representing *truth*) and BOT (for bottom, representing *falsehood*). For this algebra, the basic operators negation, conjunction and disjunction (stylized as ¬, ∧, ∨) can be defined as the complement, minimum and maximum, of the integer cast of `true` and `false`, respectively.

See also [`Truth`](@ref).
