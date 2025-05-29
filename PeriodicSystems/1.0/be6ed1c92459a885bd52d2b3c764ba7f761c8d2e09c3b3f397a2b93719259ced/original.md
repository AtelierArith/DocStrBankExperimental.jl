```
 ps2fls(psysc::PeriodicStateSpace, N; P) -> sys::DescriptorStateSpace
```

Build the frequency-lifted representation of a continuous-time periodic system.

For a continuos-time periodic system `psysc = (A(t),B(t),C(t),D(t))`, the (complex)  LTI state-space representation `sys = (At-Nt,Bt,Ct,Dt)` is built, where `At`, `Bt`, `Ct` and `Dt`  are truncated block Toeplitz matrices and `Nt` is a block diagonal matrix (see [1] or [2]).  `N` is the number of selected harmonic components in the Fourier series of system matrices  and the keyword parameter `P` is the number of full periods to be considered (default: `P = 1`). 

*References*

[1] N. M. Wereley. Analysis and control of linear periodically time varying systems.      Ph.D. thesis, Department of Aeronautics and Astronautics, MIT, 1990.

[2] S. Bittanti and P. Colaneri. Periodic Systems : Filtering and Control.     Springer-Verlag London, 2009. 
