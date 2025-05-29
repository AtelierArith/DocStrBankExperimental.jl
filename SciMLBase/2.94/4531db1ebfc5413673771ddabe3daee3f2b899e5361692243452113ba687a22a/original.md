```
reeval_internals_due_to_modification!(integrator::DEIntegrator, continuous_modification::Bool=true;
                                      callback_initializealg = nothing)
```

Update DE integrator after changes by callbacks. For DAEs (either implicit or semi-explicit), this requires re-solving alebraic variables. If continuous_modification is true (or unspecified), this should also recalculate interpolation data. Otherwise the integrator is allowed to skip recalculating the interpolation.

# Arguments

  * `continuous_modification`: determines whether the modification is due to a continuous change (continuous callback) or a discrete callback. For a continuous change, this can include a change to time which requires a re-evaluation of the interpolations.
  * `callback_initializealg`: the initialization algorithm provided by the callback. For DAEs, this is the choice for the initialization that is done post callback. The default value of `nothing` means that the initialization choice used for the DAE should be performed post-callback.
