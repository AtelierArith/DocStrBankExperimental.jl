```
power_method(x0,Hop,PARAM)
```

POWER_METHOD: Power iteration method to computes max eigenvalue of H'H               where H and H' are given by Hop. This function is               needed to evaluate the step parameter of FISTA.

# Arguments

  * `x0`:initial seed with dimensions such that H'*H*x0 does not abort
  * `Hop`:liner operator that encapsulates H and H' such that       Hop(x,PARAM, 1) = H x       Hop(y,PARAM,-1) = H'y
  * `PARAM`:parameters to run Hop and it's adjoint
