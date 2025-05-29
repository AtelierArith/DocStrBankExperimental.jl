```
bertalanffy(times, p)
```

Return volumes for specified `times`, based on the analytic solution to the General Bertalanffy model for lesion growth.  Here `p` will have properties `v0`, `v∞`, `ω`, `λ`, where `v0` is the volume at time `times[1]`. Other parameters are explained below.

Special cases of the model are:

  * [`logistic`](@ref) (`λ = -1`)
  * [`classical_bertalanffy`](@ref)  (`λ = 1/3`)
  * [`gompertz`](@ref) (`λ = 0`)

# Underlying ODE

In the General Bertalanffy model, the volume $v > 0$ evolves according to the differential equation

$dv/dt = ω B_λ(v_∞/v) v,$

where $B_λ$ is the Box-Cox transformation, defined by $B_λ(x) = (x^λ - 1)/λ$, unless $λ = 0$, in which case, $B_λ(x) = \log(x)$. Here:

  * $v_∞$=`v∞` is the steady state solution, stable and unique, assuming $ω >  0$; this is sometimes referred to as the *carrying capacity*
  * $1/ω$ has the  units of time
  * $λ$ is dimensionless

For a list of all models see [`TumorGrowth`](@ref). 
