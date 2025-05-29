```
pharmaPCSAFTModel <: PCSAFTModel

pharmaPCSAFT(components;
idealmodel = BasicIdeal,
userlocations = String[],
ideal_userlocations = String[],
reference_state = nothing,
verbose = false,
assoc_options = AssocOptions())
```

## Input parameters

  * `Mw`: Single Parameter (`Float64`) - Molecular Weight `[g/mol]`
  * `segment`: Single Parameter (`Float64`) - Number of segments (no units)
  * `sigma`: Single Parameter (`Float64`) - Segment Diameter [`A°`]
  * `epsilon`: Single Parameter (`Float64`) - Reduced dispersion energy  `[K]`
  * `k`: Pair Parameter (`Float64`) (optional) - Constant binary Interaction Paramater (no units)
  * `kT`: Pair Parameter (`Float64`) - T-dependent inary Interaction Paramater `[K^-1]`
  * `epsilon_assoc`: Association Parameter (`Float64`) - Reduced association energy `[K]`
  * `bondvol`: Association Parameter (`Float64`) - Association Volume `[m^3]`

## Model Parameters

  * `Mw`: Single Parameter (`Float64`) - Molecular Weight `[g/mol]`
  * `segment`: Single Parameter (`Float64`) - Number of segments (no units)
  * `sigma`: Pair Parameter (`Float64`) - Mixed segment Diameter `[m]`
  * `epsilon`: Pair Parameter (`Float64`) - Mixed reduced dispersion energy`[K]`
  * `k`: Pair Parameter (`Float64`) (optional) - Constant binary Interaction Paramater (no units)
  * `kT`: Pair Parameter (`Float64`) - T-dependent inary Interaction Paramater `[K^-1]`
  * `epsilon_assoc`: Association Parameter (`Float64`) - Reduced association energy `[K]`
  * `bondvol`: Association Parameter (`Float64`) - Association Volume

## Input models

  * `idealmodel`: Ideal Model

## Description

Perturbed-Chain SAFT (PC-SAFT), with T dependent kij and water correlation [2] for segment diameter. For using the water's sigma correlation, `water08` should be selected instead of `water`.

## References

1. Paus, R., Ji, Y., Vahle, L., & Sadowski, G. (2015). Predicting the solubility advantage of amorphous pharmaceuticals: A novel thermodynamic approach. Molecular Pharmaceutics, 12(8), 2823–2833. [doi:10.1021/mp500824d](https://doi.org/10.1021/mp500824d)
2. Cameretti, L. F., & Sadowski, G. (2008). Modeling of aqueous amino acid and polypeptide solutions with PC-SAFT. Genie Des Procedes [Chemical Engineering and Processing], 47(6), 1018–1025. [doi:10.1016/j.cep.2007.02.034](https://doi.org/10.1016/j.cep.2007.02.034)
