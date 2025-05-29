```
SpinSqueezing(ρ::AbstractMatrix; basis="Dicke", output="KU")
```

Calculate the spin squeezing parameter for the input density matrix. The `basis` can be `"Dicke"` for the Dicke basis, or `"Pauli"` for the Pauli basis. The `output` can be both `"KU"`(for spin squeezing defined by Kitagawa and Ueda) and `"WBIMH"`(for spin squeezing defined by Wineland et al.).
