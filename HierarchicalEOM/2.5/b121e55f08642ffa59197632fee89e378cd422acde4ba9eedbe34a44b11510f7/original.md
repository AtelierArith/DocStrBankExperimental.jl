```
struct Exponent <: BathTerm
```

An object which describes a single exponential-expansion term (naively, an excitation mode) within the decomposition of the bath correlation functions.

The expansion of a bath correlation function can be expressed as : $C(t) = \sum_i \eta_i \exp(-\gamma_i t)$.

# Fields

  * `op::QuantumObject` : The system coupling operator according to system-bath interaction.
  * `η::Number` : the coefficient $\eta_i$ in bath correlation function.
  * `γ::Number` : the coefficient $\gamma_i$ in bath correlation function.
  * `types::String` : The type-tag of the exponent.

The different types of the Exponent:

  * `"bR"` : from real part of bosonic correlation function $C^{u=\textrm{R}}(t)$
  * `"bI"` : from imaginary part of bosonic correlation function $C^{u=\textrm{I}}(t)$
  * `"bRI"` : from combined (real and imaginary part) bosonic bath correlation function $C(t)$
  * `"bA"` : from absorption bosonic correlation function $C^{\nu=+}(t)$
  * `"bE"` : from emission bosonic correlation function $C^{\nu=-}(t)$
  * `"fA"` : from absorption fermionic correlation function $C^{\nu=+}(t)$
  * `"fE"` : from emission fermionic correlation function $C^{\nu=-}(t)$
