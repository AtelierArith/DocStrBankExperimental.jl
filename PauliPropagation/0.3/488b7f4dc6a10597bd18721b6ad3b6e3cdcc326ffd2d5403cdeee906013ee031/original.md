```
set!(psum::Dict{TermType, NodePathProperties}, pstr::TermType, path::NodePathProperties)
```

In-place setting the coefficient of a Pauli string in a Pauli sum dictionary. The type of the Pauli string needs to be the keytype=`TermType` of the dictionary, and the coefficient `coeff` needs to be the valuetype=`NodePathProperties`. If the coefficient is 0, the Pauli string is removed from the dictionary.
