```
PeriodicStateSpace(A::PM, B::PM, C::PM, D::PM) -> psys::PeriodicStateSpace{PM}
```

Construct a `PeriodicStateSpace` object from a quadruple of periodic matrix objects. 

The periodic matrix objects `A`, `B`, `C`, `D` specifies the periodic matrices `A(t)`, `B(t)`, `C(t)` and `D(t)` of a linear periodic time-varying state space model in the continuous-time form

```
 dx(t)/dt = A(t)x(t) + B(t)u(t) ,
 y(t)     = C(t)x(t) + D(t)u(t) ,
```

or in the discrete-time form

```
 x(t+1)  = A(t)x(t) + B(t)u(t) ,
 y(t)    = C(t)x(t) + D(t)u(t) ,
```

where `x(t)`, `u(t)` and `y(t)` are the system state vector,  system input vector and system output vector, respectively,  and `t` is the continuous or discrete time variable.  The system matrices satisfy `A(t) = A(t+T₁)`, `B(t) = B(t+T₂)`, `C(t) = C(t+T₃)`, `D(t) = D(t+T₄)`,   i.e., are periodic with periods `T₁`, `T₂`, `T₃` and `T₄`, respectively.  The different periods must be commensurate (i.e., their ratios must be rational numbers with numerators and denominators up to at most 4 decimal digits).  All periodic matrix objects must have the same type `PM`, where `PM` stays for one of the supported periodic matrix types, i.e.,  `PeriodicMatrix`, `SwitchingPeriodicMatrix`, `PeriodicArray`, `SwitchingPeriodicArray`,  `PeriodicFunctionMatrix`, `PeriodicSymbolicMatrix`, `HarmonicArray`, `FourierFunctionMatrix`, `PeriodicTimeSeriesMatrix` or `PeriodicSwitchingMatrix`. 
