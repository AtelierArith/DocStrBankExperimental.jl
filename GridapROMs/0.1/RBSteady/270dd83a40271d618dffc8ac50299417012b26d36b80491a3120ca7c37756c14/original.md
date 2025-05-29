```
struct SupremizerReduction{A,R<:Reduction{A,EnergyNorm}} <: Reduction{A,EnergyNorm}
  reduction::R
  supr_op::Function
  supr_tol::Float64
end
```

Wrapper for reduction methods `reduction` that require an additional step of stabilization, by means of a supremizer enrichment. Check [this](https://doi.org/10.1002/nme.4772) for more details in a steady setting, and [this](https://doi.org/10.1137/22M1509114) for more details in a transient setting. The fields `supr_op` and `supr_tol` (which is only needed only in transient applications) are respectively the supremizing operator and the tolerance involved in the enrichment. For a saddle point problem with a Jacobian of the form

[ A   Bᵀ   B   0 ]

this operator is given by the bilinear form representing the matrix Bᵀ.
