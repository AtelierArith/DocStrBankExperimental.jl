```
chemical_potentials!(μ,u,electrolyte)
```

Calculate chemical potentials from concentrations.

Input:

  * `μ`: memory for result (will be filled)
  * `u`: local solution vector (concentrations, potential, pressure)

Returns `μ0, μ`: chemical potential of solvent and chemical potentials of ions.

```jldoctest
using LessUnitful
ely = ElectrolyteData(c_bulk = fill(0.01ufac"mol/dm^3", 2))
μ0, μ = chemical_potentials!([0.0, 0.0], vcat(ely.c_bulk, [0, 0]), ely)
round(μ0, sigdigits = 5), round.(μ, sigdigits = 5)
# output

(-0.89834, [-21359.0, -21359.0])
```

!!! note "Breaking change between v0.2 and 0.3"
    This function has been corrected in version 0.3.  Before it used the molar volume $v$ instead of the effective molar volume $\bar v = v + κv_0$ to calculate the ion chemical potentials. Examples with κ=0 are not affected.

