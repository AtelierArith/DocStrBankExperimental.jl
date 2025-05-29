```
SAFTgammaMie <: SAFTModel
```

SAFTgammaMie(components;     idealmodel = BasicIdeal,     userlocations = String[],     group*userlocations = String[],     ideal*userlocations = String[],     epsilon*mixing = :default,     reference*state = nothing,     verbose = false,     assoc_options = AssocOptions())

## Input parameters

  * `Mw`: Single Parameter (`Float64`) - Molecular Weight `[g/mol]`
  * `vst`: Single Parameter (`Float64`) - Number of segments (no units)
  * `S`: Single Parameter (`Float64`) - Shape factor for segment (no units)
  * `sigma`: Single Parameter (`Float64`) - Segment Diameter [`A°`]
  * `epsilon`: Single Parameter (`Float64`) - Reduced dispersion energy  `[K]`
  * `lambda_a`: Pair Parameter (`Float64`) - Atractive range parameter (no units)
  * `lambda_r`: Pair Parameter (`Float64`) - Repulsive range parameter (no units)
  * `epsilon_assoc`: Association Parameter (`Float64`) - Reduced association energy `[K]`
  * `bondvol`: Association Parameter (`Float64`) - Association Volume

## Model Parameters

  * `segment`: Single Parameter (`Float64`) - Number of segments (no units)
  * `shapefactor`: Single Parameter (`Float64`) - Shape factor for segment (no units)
  * `sigma`: Pair Parameter (`Float64`) - Mixed segment Diameter `[m]`
  * `lambda_a`: Pair Parameter (`Float64`) - Atractive range parameter (no units)
  * `lambda_r`: Pair Parameter (`Float64`) - Repulsive range parameter (no units)
  * `epsilon`: Pair Parameter (`Float64`) - Mixed reduced dispersion energy`[K]`
  * `epsilon_assoc`: Association Parameter (`Float64`) - Reduced association energy `[K]`
  * `bondvol`: Association Parameter (`Float64`) - Association Volume
  * `mixed_segment`: Mixed Group Contribution Parameter: ∑nᵢₖνₖmₖ

## Input models

  * `idealmodel`: Ideal Model

## Description

SAFT-γ-Mie EoS

!!! info
    You can choose between the Hudsen-McCoubrey combining rule (`√(ϵᵢ*ϵⱼ)*(σᵢ^3 * σⱼ^3)/σᵢⱼ^6`) or the default rule (`√(ϵᵢ*ϵⱼ*(σᵢ^3 * σⱼ^3))/σᵢⱼ^3`) by passing the `epsilon_mixing` argument. with arguments `:default` or `:hudsen_mccoubrey`


## References

1. Papaioannou, V., Lafitte, T., Avendaño, C., Adjiman, C. S., Jackson, G., Müller, E. A., & Galindo, A. (2014). Group contribution methodology based on the statistical associating fluid theory for heteronuclear molecules formed from Mie segments. The Journal of Chemical Physics, 140(5), 054107. [doi:10.1063/1.4851455](https://doi.org/10.1063/1.4851455)
2. Dufal, S., Papaioannou, V., Sadeqzadeh, M., Pogiatzis, T., Chremos, A., Adjiman, C. S., … Galindo, A. (2014). Prediction of thermodynamic properties and phase behavior of fluids and mixtures with the SAFT-γ Mie group-contribution equation of state. Journal of Chemical and Engineering Data, 59(10), 3272–3288. [doi:10.1021/je500248h](https://doi.org/10.1021/je500248h)

## List of available groups

|   Name |              Description |
| ------:| ------------------------:|
|    CH3 |                   Methyl |
|    CH2 |                Methylene |
|     CH |                          |
|      C |                          |
|    aCH |              Aromatic CH |
|  aCCH2 |                          |
|   aCCH |                          |
|   CH2= |             Alkene group |
|    CH= |                          |
|   cCH2 |      Cyclic alkane group |
|   COOH |    Carboxylic acid group |
|    COO |              Ester group |
|     OH |                 Hydroxyl |
|  CH2OH | Methylene hydroxyl group |
|   CHOH |                          |
|    NH2 |              Amine group |
|     NH |                          |
|      N |                          |
|    cNH |                          |
|     cN |                          |
|    CH= |                          |
|  aCCH3 |                          |
|   aCOH |                          |
|    cCH |                          |
|  cCHNH |                          |
|   cCHN |                          |
| aCCOaC |                          |
| aCCOOH |                          |
| aCNHaC |                          |
|  CH3CO |                          |
|     eO |         End ether oxygen |
|     cO |      Center ether oxygen |
