```
act_on_ket(::Operator)
```

All typed extending `Operator` must overload this function. It should return the expression you end up with after acting the operator on a normal RHF ket.

Example:

$E_{p q} |HF⟩ = (2 δ_{p q} C(p∈O,q∈O) + E_{p q} C(p∈V,q∈O)) |HF⟩$
