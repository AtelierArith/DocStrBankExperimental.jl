```
UNIQUACModel <: ActivityModel

UNIQUAC(components;
puremodel = PR,
userlocations = String[], 
pure_userlocations = String[],
verbose = false,
reference_state = nothing)
```

## Input parameters

  * `a`: Pair Parameter (`Float64`, asymetrical, defaults to `0`) - Binary Interaction Energy Parameter
  * `r`: Single Parameter (`Float64`)  - Normalized Van der Vals volume
  * `q`: Single Parameter (`Float64`) - Normalized Surface Area
  * `q_p`: Single Parameter (`Float64`) - Modified Normalized Surface Area
  * `Mw`: Single Parameter (`Float64`) - Molecular Weight `[g/mol]`

## Input models

  * `puremodel`: model to calculate pure pressure-dependent properties

UNIQUAC (Universal QuasiChemical Activity Coefficients) activity model:

```
Gᴱ = nRT(gᴱ(comb) + gᴱ(res))
gᴱ(comb) = ∑[xᵢlog(Φᵢ/xᵢ) + 5qᵢxᵢlog(θᵢ/Φᵢ)]
gᴱ(res) = -∑xᵢqᵖᵢlog(∑θᵖⱼτⱼᵢ)
θᵢ = qᵢxᵢ/∑qᵢxᵢ
θᵖ = qᵖᵢxᵢ/∑qᵖᵢxᵢ
Φᵢ = rᵢxᵢ/∑rᵢxᵢ
τᵢⱼ = exp(-aᵢⱼ/T)
```

## Model Construction Examples

```
# Using the default database
model = UNIQUAC(["water","ethanol"]) #Default pure model: PR
model = UNIQUAC(["water","ethanol"],puremodel = BasicIdeal) #Using Ideal Gas for pure model properties
model = UNIQUAC(["water","ethanol"],puremodel = PCSAFT) #Using Real Gas model for pure model properties

# Passing a prebuilt model

my_puremodel = AbbottVirial(["water","ethanol"]; userlocations = ["path/to/my/db","critical.csv"])
mixing = UNIQUAC(["water","ethanol"],puremodel = my_puremodel)

# Using user-provided parameters

# Passing files or folders
model = UNIQUAC(["water","ethanol"];userlocations = ["path/to/my/db","uniquac_ge.csv"])

# Passing parameters directly
model = UNIQUAC(["water","ethanol"],
        userlocations = (a = [0.0 378.1; 258.4 0.0], 
                        r = [0.92, 2.11],
                        q = [1.4, 1.97],
                        q_p = [1.0, 0.92],
                        Mw = [18.015, 46.069])
                    )
```

## References

1. Abrams, D. S., & Prausnitz, J. M. (1975). Statistical thermodynamics of liquid mixtures: A new expression for the excess Gibbs energy of partly or completely miscible systems. AIChE journal. American Institute of Chemical Engineers, 21(1), 116–128. [doi:10.1002/aic.690210115](https://doi.org/10.1002/aic.690210115)
