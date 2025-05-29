```
save_parameters!(integrator::SciMLBase.DEIntegrator)
```

Save the current parameter values in the integrator. Call this function inside callbacks if the parameter values have changed. This will store a timeseries of said parameters in the solution object, thus alowing us to recosntruct observables which depend on time-dependet variables.
