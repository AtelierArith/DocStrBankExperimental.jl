```
ASM1(; name, Y_H=0.67, Y_A=0.24, i_XB=0.086, i_XP=0.01, f_P=0.08, mu_H=6.0, K_S=20.0, K_OH=0.2, K_NO=0.5, b_H=0.62,
     eta_g=0.8, mu_A=0.8, K_NH=1.0, K_OA=0.4, b_A=0.1, kappa_h=3.0, eta_h=0.4, K_X=0.03, kappa_a=0.08)
```

A component that defines the process rate in the activated sludge model number 1 (ASM1). Taken from [Henze:2006](@cite)

!!! warning "Initial State"
    When using this Model, one needs to set the initial state/initial condition **in the corresponding reactor**. This is because the default values are all `0`, and the some of the process equations have a division by `0` if all states are `0`!


# Parameters:

  * stoichiometric parameter (all at 20 C, neutral pH):

      * `Y_H` heterotrophic yield (default 0.67 gCOD/gCOD)
      * `Y_A` autotrophic yield (default 0.24 gCOD/gCOD)
      * `i_XB` nitrogen fraction in biomass (default 0.086 gN/gCOD)
      * `i_XP` nitrogen fraction in endogenous mass (default 0.01 gN/gCOD)
      * `f_P` fraction of biomass leading to particulate material (default 0.08 -)
  * kinetic parameter heterotrophs:

      * `mu_H` maximum specific growth rate (default 6.0 1/day)
      * `K_S` substrate saturation constant (default 20.0 gCOD/m3)
      * `K_OH` Oxygen saturation constant (default 0.2 gO2/m3)
      * `K_NO` nitrate saturation constant (default 0.5 gNO3-N/m3)
      * `b_H` specific decay rate (default 0.62 1/day)
      * `eta_g` anoxic growth correction factor (default 0.8 -)
  * kinetic parameter autotrophs:

      * `mu_A` maximum specific growth rate (default 0.8 1/day)
      * `K_NH` ammonium saturation constant (default 1.0 gO2/m3)
      * `K_OA` oxygen saturation constant (default 0.4 gO2/m3)
      * `b_A` specific decay rate (default 0.1 1/day)
  * hydrolysis parameter

      * `kappa_h` maximum specific hydrolysis rate (default 3.0 1/day)
      * `eta_h` anoxic hydrolysis correction factor (default 0.4 -)
      * `K_X` half-saturation coefficient for hydrolysis of XS (default 0.03 -)
  * ammonification

      * `kappa_a` ammonification rate constant (default 0.08 m3/(gCOD*day))

# States:

  * `S_I`   soluble inert organic matter
  * `S_S`   readily biodegradable substrate
  * `S_O`   oxygen
  * `S_NO`  nitrate and nitrite nitrogen
  * `S_NH`  ammonium and ammonia nitrogen
  * `S_ND`  soluble biodegradable organic nitrogen
  * `S_ALK` alkalinity
  * `X_I`   particulate inert organic matter
  * `X_S`   slowly biodegradable substrate
  * `X_BH`  active heterotrophic biomass
  * `X_BA`  active autotrophic biomass
  * `X_P`   particulate products from biomass decay
  * `X_ND`  particulate biodegradable organic
