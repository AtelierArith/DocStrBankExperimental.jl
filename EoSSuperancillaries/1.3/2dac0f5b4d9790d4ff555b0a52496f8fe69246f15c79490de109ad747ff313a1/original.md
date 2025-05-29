```
Θ,status = pcsaft_theta(T̃,m)
Θ,status = pcsaft_theta(T̃,m,T̃c)
```

Calculates reduced scaled temperature parameter used in PCSAFT saturation volume superancillary

Inputs:

  * `T̃`: Temperature divided by reduced interaction energy (`T/ϵ`) (no units)
  * `m`: Segment length (no units)
  * `T̃c`: (Optional) Reduced critical temperature (`Tc/ϵ`) (no units)

Outputs:

  * `Θ` : scaled temperature parameter (no units)
  * `status` : `Symbol` used to signal if the combination of `T̃`,`m` is valid or not. It can return one of the following:

      * `:inrange` : if the combination is valid
      * `:nonfinite` : if any input is not finite
      * `:below_mmin` : if `m` < 1.0
      * `:over_mmax` : if `m` > 64.0
      * `:below_Tmin` : if `T̃` < `T̃min`, where `T̃min` = `T̃c*exp(-2.20078778)*m^0.37627892`
      * `:over_Tmax` : if `T̃` > `T̃c`
