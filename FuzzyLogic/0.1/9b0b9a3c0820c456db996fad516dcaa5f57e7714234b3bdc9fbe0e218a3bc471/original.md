```julia
struct HamacherAnd <: FuzzyLogic.AbstractAnd
```

Hamacher T-norm defining conjuction as $A ∧ B = \frac{AB}{A + B - AB}$ if $A \neq 0 \neq B$ and $A ∧ B = 0$ otherwise.
