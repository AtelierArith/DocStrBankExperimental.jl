```
NLLSsolver.computecostgradhess(varflags, mycost, vars...)
```

Compute the cost generated by `mycost`, and its first and second derivatives w.r.t. the  variables indicated by the set bits in varflags (the first bit corresponds to the first  variable, and so on) given the variables `vars`. The return values must be a scalar, vector  and matrix.

!!! tip
    Try using the default autodiff function before specializing this function for your type.


!!! note
    Optional user-specialized API function.

