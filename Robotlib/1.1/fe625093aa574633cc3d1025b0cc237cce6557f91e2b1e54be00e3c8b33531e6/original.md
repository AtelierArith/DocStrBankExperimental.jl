```
calibLPOEdual(xi,Tn0,q;maxiter=10, λ=1.0)
```

Performs dual arm calibration given joint twists xi and nominal transformations Tn0 Returns calibrated nominal transformations. This function does not converge to the correct kinematic parameters since the problem is underspecified. It only converges to kinematic parameters that make the two arms agree.
