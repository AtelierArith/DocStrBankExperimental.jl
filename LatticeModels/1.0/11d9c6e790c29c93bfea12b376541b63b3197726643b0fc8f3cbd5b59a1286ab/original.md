```
projector(f, eig::Eigensystem)
```

Returns an `Operator` representing a function applied to the diagonalized operator defined by the formula below:

$\hat{\mathcal{P}} = \sum_i f(A_i) |\psi_i⟩⟨\psi_i|$
