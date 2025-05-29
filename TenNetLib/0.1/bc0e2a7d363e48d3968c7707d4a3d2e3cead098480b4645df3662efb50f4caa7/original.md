```
mutable struct ProjMPS2 <: AbstractProjMPO
    lpos::Int
    rpos::Int
    nsite::Int
    M::MPS
    LR::Vector{ITensor}
end
```

Holds the following data where `psi` is the MPS being optimized and `M` is the  MPS held constant by the ProjMPS.

Inherited from `AbstractProjMPO` from `ITesnors.jl`.

```
     o--o--o--o--o--o--o--o--o--o--o <M|
     |  |  |  |  |  |  |  |  |  |  |
     *--*--*-      -*--*--*--*--*--* |psi>
```

Required for calculating projectors for a MPS.
