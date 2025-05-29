```
 ps2frls(psysc::PeriodicStateSpace, N) -> sys::DescriptorStateSpace
```

Build the real frequency-lifted representation of a continuous-time periodic system.

For a continuos-time periodic system `psysc = (A(t),B(t),C(t),D(t))`, the real  LTI state-space representation `sys = (At-Nt,Bt,Ct,Dt)` is built, where `At`, `Bt`, `Ct` and `Dt`  are truncated block Toeplitz matrices and `Nt` is a block diagonal matrix.  `N` is the number of selected harmonic components in the Fourier series of system matrices. 

*Note:* This is an experimental implementation based on the operator representation of periodic matrices in the [ApproxFun.jl](https://github.com/JuliaApproximation/ApproxFun.jl) package. 
