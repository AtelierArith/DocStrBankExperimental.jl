```
ShiftOperator{BL,BR}(basis_l, basis_r, shift)
```

Dense shift operator as a mutable struct using the definition

$D(\alpha) = \exp(\alpha a^\dagger - \alpha^* a)$.

# Arguments

  * `basis_l`: Bra basis.
  * `basis_r`: Ket basis.
  * `shift`: Shift or $\alpha$ parameter, can be complex number.
