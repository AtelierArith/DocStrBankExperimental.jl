```
 ps2spls(psys::PeriodicStateSpace[, kstart]; cyclic = false) -> sys::DescriptorStateSpace
```

Build the discrete-time lifted LTI system equivalent to a discrete-time periodic system. 

For a discrete-time periodic system `psys = (A(t),B(t),C(t),D(t))` with period `T` and sample time `Ts`,  the equivalent stacked (see [1]) LTI descriptor state-space representation  `sys = (As-λEs,Bs,Cs,Ds)` is built, with the input, state and output vectors defined over time intervals of length `T` (instead `Ts`).   The optional argument `kstart` specifies a desired time to start the sequence of periodic matrices (default: `kstart = 1`). The matrices `As`, `Es`, `Bs`, `Cs` and `Ds` are sparce matrices as defined within the  [SparseArrays.jl](https://github.com/JuliaSparse/SparseArrays.jl) package. 

If `cyclic = true`, the cyclic reformulation of [2] is used to build a lifted standard system with  the input, state and output vectors defined over time intervals of length `T`.

*References*

[1] O. M. Grasselli and S. Longhi. Finite zero structure of linear periodic discrete-time systems.      Int. J. Systems Sci., 22:1785–1806,  1991.

[2] D. S. Flamm. A new shift-invariant representation for periodic systems,      Systems and Control Letters, 17:9–14, 1991.
