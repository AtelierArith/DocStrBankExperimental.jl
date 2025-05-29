```
 ps2ls(psys::PeriodicStateSpace[, kstart]; ss = false, cyclic = false) -> sys::DescriptorStateSpace
```

Build the discrete-time lifted LTI system equivalent to a discrete-time periodic system. 

For a discrete-time periodic system `psys = (A(t),B(t),C(t),D(t))` with period `T` and sample time `Ts`,  the equivalent stacked (see [1]) LTI descriptor state-space representation  `sys = (A-λE,B,C,D)` is built, with the input, state and output vectors defined over time intervals of length `T` (instead `Ts`).   The optional argument `kstart` specifies a desired time to start the sequence of periodic matrices (default: `kstart = 1`).

If `ss = true` (default: `ss = false`), then all non-dynamic modes are elliminated and  a standard state-space realization (with `E = I`) is determined, which corresponds to the lifting techniques of [2], where only the input and output vectors are defined over time intervals of length `T`.  The determination of the standard lifted representation involves forming matrix products  (e.g., by explicitly forming the monodromy matrix) and therefore is potentially less suited for numerical computations.  

If `cyclic = true`, the cyclic reformulation of [3] is used to build a lifted standard system with  the input, state and output vectors defined over time intervals of length `T`.

*References*

[1] O. M. Grasselli and S. Longhi. Finite zero structure of linear periodic discrete-time systems.      Int. J. Systems Sci., 22:1785–1806,  1991.

[2] R. A. Meyer and C. S. Burrus. A unified analysis of multirate and periodically time-varying     digital filters”, IEEE Transactions on Circuits and Systems, 22:162–167, 1975.

[3] D. S. Flamm. A new shift-invariant representation for periodic systems,      Systems and Control Letters, 17:9–14, 1991.
