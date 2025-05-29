```
 psmrc2d(sys, Ts; ki, ko) -> psys::PeriodicStateSpace{PeriodicMatrix}
```

Perform the multirate discretization of a linear time-invariant system.

For a continuous-time state-space system `sys = (A,B,C,D)`, a basic sampling time `Ts`,  and the integer vectors `ki` and `ko` containing, respectively, the numbers of  input and output sampling subperiods, the corresponding discretized  periodic system `psys = (Ap,Bp,Cp,Dp)` of period `T = n*Ts` is determined,  where `n` is the least common multiple of the integers contained in `ki` and `ko`. For a continuous-time system `sys`  a zero-order hold based discretization method is used, such that the `i`-th input  is constant during intervals of length `ki[i]*Ts`.  An output hold device is used to provide constant intersample outputs, such that the `i`-th output is constant during intervals of length `ko[i]*Ts`.  For a discrete-time system with a defined sample time `Δ`,  an input and output resampling is performed using `Δ` as basic   sample time and the value of `Ts` is ignored.  If the system sample time is not defined, then the value of `Ts` is used as the basic sample time. 
