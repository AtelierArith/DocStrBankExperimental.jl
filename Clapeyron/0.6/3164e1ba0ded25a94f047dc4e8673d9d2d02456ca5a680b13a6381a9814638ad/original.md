```
JobackIdeal <: JobackIdealModel

JobackIdeal(components; 
userlocations = String[],
reference_state = nothing,
verbose = false)
```

## Input parameters

  * `Mw`: Single Parameter (`Float64`) - Molecular Weight `[g/mol]`
  * `N_a`: Single Parameter (`Float64`)
  * `T_c`: Single Parameter (`Float64`)
  * `P_c`: Single Parameter (`Float64`)
  * `V_c`: Single Parameter (`Float64`)
  * `T_b`: Single Parameter (`Float64`)
  * `T_m`: Single Parameter (`Float64`)
  * `H_form`: Single Parameter (`Float64`)
  * `G_form`: Single Parameter (`Float64`)
  * `a`: Single Parameter (`Float64`)
  * `b`: Single Parameter (`Float64`)
  * `c`: Single Parameter (`Float64`)
  * `d`: Single Parameter (`Float64`)
  * `H_fusion`: Single Parameter (`Float64`)
  * `H_vap`: Single Parameter (`Float64`)
  * `eta_a`: Single Parameter (`Float64`)
  * `eta_b`: Single Parameter (`Float64`)

## Description

Joback Group Contribution Ideal Model. GC version of `ReidIdeal`. Helmholtz energy obtained via integration of specific heat capacity:

```
aᵢ = ∑(νᵢₖbₖ) - 37.93
bᵢ = ∑(νᵢₖbₖ) + 0.210
cᵢ = ∑(νᵢₖcₖ) - 3.91e-4
dᵢ = ∑(νᵢₖbₖ) + 2.06e-7
Cpᵢ(T) = aᵢ  + bᵢT + cᵢT^2 + dᵢT^3
```

The GC-averaged Reid Model is available by using `ReidIdeal(model::JobackIdeal)`.

The estimated critical point of a single component can be obtained via `crit_pure(model::JobackIdeal)`

## References

1. Joback, K. G., & Reid, R. C. (1987). Estimation of pure-component properties from group-contributions. Chemical Engineering Communications, 57(1–6), 233–243. [doi:10.1080/00986448708960487](https://doi.org/10.1080/00986448708960487)

## List of available groups

|                 Name |     Description |
| --------------------:| ---------------:|
|                 -CH3 |          Methyl |
|                -CH2- |       Methylene |
|                 >CH- |                 |
|                  >C< |                 |
|              CH2=CH- |                 |
|              -CH=CH- |                 |
|                  =C< |                 |
|                  =C= |                 |
|                   CH |                 |
|                    C |                 |
|            ring-CH2- |   Cyclic alkane |
|             ring>CH- |                 |
|              ring>C< |                 |
|             ring=CH- |  Aromatic group |
|              ring=C< |                 |
|                   -F |        Fluoride |
|                  -Cl |        Chloride |
|                  -Br |         Bromide |
|                   -I |          Iodide |
|        -OH (alcohol) |  Hydroxyl group |
|         -OH (phenol) |                 |
|       -O- (non-ring) |                 |
|           -O- (ring) |                 |
|      >C=O (non-ring) |          Ketone |
|          >C=O (ring) |                 |
|     O=CH- (aldehyde) |        Aldehyde |
|         -COOH (acid) | Carboxylic acid |
|        -COO- (ester) |           Ester |
| O (other than above) |          Ketone |
|                 -NH2 |           Amine |
|       >NH (non-ring) |                 |
|           >NH (ring) |                 |
|       >N- (non-ring) |                 |
|       -N= (non-ring) |                 |
|           -N= (ring) |                 |
|                  =NH |                 |
|                  -CN |         Nitrile |
|                 -NO3 |       Nitroxide |
|                  -SH |                 |
|       -S- (non-ring) |                 |
|           -S- (ring) |                 |
