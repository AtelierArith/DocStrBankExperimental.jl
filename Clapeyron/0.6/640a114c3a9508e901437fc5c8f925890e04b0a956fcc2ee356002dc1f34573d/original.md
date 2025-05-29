```
gcPCPSAFTModel <: PCSAFTModel

HeterogcPCPSAFT(components; 
idealmodel = BasicIdeal,
userlocations = String[],
ideal_userlocations = String[],
reference_state = nothing,
verbose = false,
assoc_options = AssocOptions())
```

## Input parameters

  * `Mw`: Single Parameter (`Float64`) - Molecular Weight `[g/mol]`
  * `m`: Single Parameter (`Float64`) - Number of segments (no units)
  * `sigma`: Single Parameter (`Float64`) - Segment Diameter [`A°`]
  * `epsilon`: Single Parameter (`Float64`) - Reduced dispersion energy  `[K]`
  * `dipole`: Single Parameter (`Float64`) - Dipole moment `[D]`
  * `k`: Pair Parameter (`Float64`) - Binary Interaction Paramater (no units)
  * `epsilon_assoc`: Association Parameter (`Float64`) - Reduced association energy `[K]`
  * `bondvol`: Association Parameter (`Float64`) - Association Volume `[m^3]`

## Model Parameters

  * `Mw`: Single Parameter (`Float64`) - Molecular Weight `[g/mol]`
  * `segment`: Single Parameter (`Float64`) - Number of segments (no units)
  * `sigma`: Pair Parameter (`Float64`) - Mixed segment Diameter `[m]`
  * `epsilon`: Pair Parameter (`Float64`) - Mixed reduced dispersion energy`[K]`
  * `dipole`: Single Parameter (`Float64`) - Dipole moment `[D]`
  * `epsilon_assoc`: Association Parameter (`Float64`) - Reduced association energy `[K]`
  * `bondvol`: Association Parameter (`Float64`) - Association Volume

## Input models

  * `idealmodel`: Ideal Model

## Description

Heterosegmented Group-contribution Polar Perturbed-Chain SAFT (Hetero-gc-PCP-SAFT)

## References

1. Gross, J., Spuhl, O., Tumakaka, F. & Sadowski, G. (2003). Modeling Copolymer Systems Using the Perturbed-Chain SAFT Equation of State. Industrial & Engineering Chemistry Research, 42, 1266-1274. [doi:10.1021/ie020509y](https://doi.org/10.1021/ie020509y)
2. Sauer, E., Stavrou, M. & Gross, J. (2014). Comparison between a Homo- and a Heterosegmented Group Contribution Approach Based on the Perturbed-Chain Polar Statistical Associating Fluid Theory Equation of State. Industrial & Engineering Chemistry Research, 53(38), 14854–14864. [doi:10.1021/ie502203w](https://doi.org/10.1021/ie502203w)

## List of available groups

|     Name |          Description |
| --------:| --------------------:|
|      CH3 |               Methyl |
|      CH2 |            Methylene |
|       CH |                      |
|        C |                      |
|     CH2= |      Terminal alkene |
|      CH= |                      |
|      =C< |                      |
|     C#CH |      Terminal alkyne |
| cCH2_pen | Cyclic pentane group |
|  cCH_pen |                      |
| cCH2_hex |  Cyclic hexane group |
|  cCH_hex |                      |
|      aCH |       Aromatic group |
|      aCH |                      |
|       OH |       Hydroxyl group |
|      NH2 |          Amine group |
