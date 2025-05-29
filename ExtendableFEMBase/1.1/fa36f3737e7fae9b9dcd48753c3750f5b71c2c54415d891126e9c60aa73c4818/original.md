```julia
ReconstructionHandler(
    FES::ExtendableFEMBase.FESpace{Tv, Ti, FE1, APT},
    FES_Reconst::ExtendableFEMBase.FESpace{Tv, Ti, FE2, APT},
    AT,
    EG
) -> ExtendableFEMBase.ReconstructionHandler

```

generates a reconstruction handler returns the local coefficients need to evaluate a reconstruction operator of one finite element space into another
