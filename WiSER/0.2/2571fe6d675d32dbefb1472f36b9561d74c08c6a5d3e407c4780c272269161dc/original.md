```
update_wtmat!(m::WSVarLmmModel)
```

Update the observation weight matrix according to the parameter values  `m.τ` and `m.Lγ`. Update `m.β` by WLS and update the residuals accordingly.  Precompute and store various objects needed to  evaluate the objective function,  gradient, and Hessian. At return, 

  * `m.data[i].∇β  = Xi' inv(Vi) ri`
  * `m.data[i].Hββ = Xi' inv(Vi) Xi`
  * `m.∇β  = sum_i Xi' inv(Vi) ri`
  * `m.Hββ = sum_i Xi' inv(Vi) Xi`
