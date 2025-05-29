```
AbstractAdjointMethod
```

Abstract type representing the flavor of AD and adjoint to be used to compute the gradient of the cost function. There are two parts where one can play with how the gradient is propagated: the iceflow model VJP and the adjoint of the ODE solver. The VJP of the iceflow model can be computed using either AD (Zygote or Enzyme), the discrete, or the continuous adjoint of the iceflow model. As for the computation of the adjoint of the ODE solution, it can be handled by SciMLSensitivity, or computed using the adjoint implemented in ODINN.
