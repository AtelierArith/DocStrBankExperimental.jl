```
HERKFuncf(bs, js, sys, f_exi; ρb)
```

HERKFuncf construct the input function f for HERK method. It returns a forcing term, which is a summation of bias force term and joint spring-damper forcing term. The bias term includes the change of inertia effect, together with gravity and external force. If the body is a 2d body (for example a cylinder) in the fluid, buoyancy is also taken into account.
