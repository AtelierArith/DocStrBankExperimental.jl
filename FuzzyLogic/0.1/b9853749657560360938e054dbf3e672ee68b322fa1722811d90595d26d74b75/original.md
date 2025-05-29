```julia
struct HamacherOr <: FuzzyLogic.AbstractOr
```

Hamacher S-norm defining conjuction as $A ∨ B = \frac{A + B - AB}{1 - AB}$ if $A \neq 1 \neq B$ and $A ∨ B = 1$ otherwise.
