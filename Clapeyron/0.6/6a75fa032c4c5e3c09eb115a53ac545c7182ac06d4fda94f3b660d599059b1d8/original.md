```
UNIFACModel <: ActivityModel

UNIFAC(components;
puremodel = PR,
userlocations = String[],
group_userlocations = String[],
pure_userlocations = String[],
verbose = false,
reference_state = nothing)
```

## Input parameters

  * `R`: Single Parameter (`Float64`)  - Normalized group Van der Vals volume
  * `Q`: Single Parameter (`Float64`) - Normalized group Surface Area
  * `A`: Pair Parameter (`Float64`, asymetrical, defaults to `0`) - Binary group Interaction Energy Parameter
  * `B`: Pair Parameter (`Float64`, asymetrical, defaults to `0`) - Binary group Interaction Energy Parameter
  * `C`: Pair Parameter (`Float64`, asymetrical, defaults to `0`) - Binary group Interaction Energy Parameter

## Input models

  * `puremodel`: model to calculate pure pressure-dependent properties

## Description

UNIFAC (UNIQUAC Functional-group Activity Coefficients) activity model. Modified UNIFAC (Dortmund) implementation. The Combinatorial part corresponds to an GC-averaged modified [`UNIQUAC`](@ref) model. The residual part iterates over groups instead of components.

```
Gᴱ = nRT(gᴱ(comb) + gᴱ(res))
```

Combinatorial part:

```
gᴱ(comb) = ∑[xᵢlog(Φ'ᵢ) + 5qᵢxᵢlog(θᵢ/Φᵢ)]
θᵢ = qᵢxᵢ/∑qᵢxᵢ
Φᵢ = rᵢxᵢ/∑rᵢxᵢ
Φ'ᵢ = rᵢ^(0.75)/∑xᵢrᵢ^(0.75)
rᵢ = ∑Rₖνᵢₖ for k ∈ groups
qᵢ = ∑Qₖνᵢₖ for k ∈ groups
```

Residual Part:

```
gᴱ(residual) = -v̄∑XₖQₖlog(∑ΘₘΨₘₖ)
v̄ = ∑∑xᵢνᵢₖ for k ∈ groups,  for i ∈ components
Xₖ = (∑xᵢνᵢₖ)/v̄ for i ∈ components
Θₖ = QₖXₖ/∑QₖXₖ
Ψₖₘ = exp(-(Aₖₘ + BₖₘT + CₖₘT²)/T)
```

## References

1. Fredenslund, A., Gmehling, J., Michelsen, M. L., Rasmussen, P., & Prausnitz, J. M. (1977). Computerized design of multicomponent distillation columns using the UNIFAC group contribution method for calculation of activity coefficients. Industrial & Engineering Chemistry Process Design and Development, 16(4), 450–462. [doi:10.1021/i260064a004](https://doi.org/10.1021/i260064a004)
2. Weidlich, U.; Gmehling, J. A modified UNIFAC model. 1. Prediction of VLE, hE, and.gamma..infin. Ind. Eng. Chem. Res. 1987, 26, 1372–1381.

## List of groups available

|       Name |             Description |
| ----------:| -----------------------:|
|        CH3 |            Methyl group |
|        CH2 |         Methylene group |
|         CH |                         |
|          C |                         |
|     CH2=CH |                         |
|      CH=CH |                         |
|      CH2=C |                         |
|       CH=C |                         |
|        ACH |             Aromatic CH |
|         AC |                         |
|      ACCH3 |                         |
|      ACCH2 |                         |
|       ACCH |                         |
|     OH (P) |         Primary alcohol |
|      CH3OH |                Methanol |
|        H2O |                   Water |
|       ACOH |                         |
|      CH3CO |           Methyl ketone |
|      CH2CO |        Methylene ketone |
|        CHO |                         |
|     CH3COO |           Acetate group |
|     CH2COO |                         |
|       HCOO |                         |
|       CH3O |           Methoxy group |
|       CH2O |                         |
|        CHO |                         |
|        THF |         Tetrahydrofuran |
|     CH3NH2 |             Methylamine |
|     CH2NH2 |                         |
|      CHNH2 |                         |
|      CH3NH |                         |
|      CH2NH |                         |
|       CHNH |                         |
|       CH3N |                         |
|       CH2N |                         |
|      ACNH2 |                         |
|     AC2H2N |                         |
|      AC2HN |                         |
|       AC2N |                         |
|      CH3CN |            Acetonitrile |
|      CH2CN |                         |
|        COO |             Ester group |
|       COOH |       Carboxylate group |
|      HCOOH |             Formic acid |
|      CH2CL |                         |
|       CHCL |                         |
|        CCL |                         |
|     CH2CL2 |         Dichloromethane |
|      CHCL2 |                         |
|       CCL2 |                         |
|      CHCL3 |              Chloroform |
|       CCL3 |                         |
|       CCL4 |    Carbon tetrachloride |
|       ACCL |                         |
|     CH3NO2 |            Nitromethane |
|     CH2NO2 |                         |
|      CHNO2 |                         |
|      ACNO2 |                         |
|        CS2 |        Carbon disulfide |
|      CH3SH |            Methanethiol |
|      CH2SH |                         |
|   FURFURAL |                Furfural |
|        DOH |                         |
|          I |            Iodine group |
|         BR |           Bromine group |
|      CH=-C |                         |
|       C=-C |                         |
|       DMSO |      Dimethyl sulfoxide |
|       ACRY |                Acrylate |
|   CL-(C=C) |                         |
|        C=C |                         |
|        ACF |                         |
|        DMF |       Dimethylformamide |
| HCON(CH2)2 |                         |
|        CF3 |                         |
|        CF2 |                         |
|         CF |                         |
|     CY-CH2 |       Cycloalkane group |
|      CY-CH |                         |
|       CY-C |                         |
|     OH (S) |   Second hydroxyl group |
|     OH (T) | Tertiary hydroxyl group |
|    CY-CH2O |                         |
|    TRIOXAN |                Trioxane |
|       CNH2 |                         |
|        NMP |     N-Methylpyrrolidone |
|        NEP |                         |
|       NIPP |                         |
|       NTBP |                         |
|      CONH2 |                         |
|    CONHCH3 |                         |
|    CONHCH2 |                         |
