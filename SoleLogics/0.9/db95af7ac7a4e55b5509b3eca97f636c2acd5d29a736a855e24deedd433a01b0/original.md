```
(op::Operator)(o::Any)
```

An `Operator` can be used to compose syntax tokens (e.g., atoms), syntax trees and/or formulas.

# Examples

```julia-repl
    ¬(Atom(1)) ∨ Atom(1) ∧ ⊤
    ∧(⊤,⊤)
    ⊤()
```
