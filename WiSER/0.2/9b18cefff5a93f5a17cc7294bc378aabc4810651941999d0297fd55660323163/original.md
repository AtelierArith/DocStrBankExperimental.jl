```
nlsv_obj!(obs::WSVarLmmObs, β, τ, Lγ, needgrad::Bool) 
nlsv_obj!(m::WSVarLmmModel; needgrad::Bool)
```

Evaluate the nonlinear least squares (NLS) criterion for variance estimation at  the given data and parameter values. Gradient is calculated if `needgrad=true`.  Expected Hessian is calculated if `needhess=true`.  If `updateres=true`, update  mean level residuals first. If `m.iswtnls[1]=true`, evaluate the weighted `nlsv_obj!()` function. `update_wtmat!(m)` should be called to update the  weight matrix componentsprior to using the weighted version of `nlsv_obj!()`. 
