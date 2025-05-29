```
set!(psum::PauliSum{TermType, CoeffType}, pstr::TermType, coeff::CoeffType)
```

In-place setting the coefficient of a Pauli string in a `PauliSum` dictionary. The type of the Pauli string needs to be the keytype=`TermType` of the dictionary, and the coefficient `coeff` needs to be the valuetype=`CoeffType`.
