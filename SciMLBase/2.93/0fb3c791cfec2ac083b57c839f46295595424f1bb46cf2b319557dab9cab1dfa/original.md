```
savevalues!(integrator::DEIntegrator,
  force_save=false) -> Tuple{Bool, Bool}
```

Try to save the state and time variables at the current time point, or the `saveat` point by using interpolation when appropriate. It returns a tuple that is `(saved, savedexactly)`. If `savevalues!` saved value, then `saved` is true, and if `savevalues!` saved at the current time point, then `savedexactly` is true.

The saving priority/order is as follows:

  * `save_on`

      * `saveat`
      * `force_save`
      * `save_everystep`
