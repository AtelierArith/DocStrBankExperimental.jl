```
terminate!(i::DEIntegrator[, retcode = :Terminated])
```

Terminates the integrator by emptying `tstops`. This can be used in events and callbacks to immediately end the solution process.  Optionally, `retcode` may be specified (see: [Return Codes (RetCodes)](@ref retcodes)).
