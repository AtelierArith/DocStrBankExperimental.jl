```
DiscreteSystem(sysid, Phi, Gam, C, D, inputid [, Rd, Qc])
```

Create a discrete-time linear system

```
u(k) --> sys --> y(k)
         x(k)
```

The state/output initially has mean value `E([x; y]) = 0` and covariance `V([x; y]) = 0`.

## Arguments:

  * `sysid`:              A unique positive `Integer` identifier for this system (pick any). Used when referred to from other systems.
  * `[Phi, Gam, C, D]`:   A discrete-time LTI system in state-space form (if `Phi`, `Gam`, and `C` are missing, interpreted as a static gain).
  * `inputid`:            A vector of input system identifiers.                        The outputs of the corresponding systems will be used as inputs to this system.                       The number of inputs in this system must equal the total number of outputs in the input systems.                       An empty vector (or zero) indicates that the system inputs are unconnected.
  * `Rd`:                 (OPTIONAL) The discrete state/output/input noise covariance matrix.                        The noise vector is assumed to have the same size as `[x; y]` (for state-space systems).                       Noise is added each time the system is executed.                       Default assumed zero.
  * `Qc`:                 (OPTIONAL) The continuous cost function is `E(Integral [x(t); u(t)]' * Qc * [x(t); u(t)] dt)` (for state-space systems).                       *Note* that both `x(t)` and `y(t)` are held constant between system executions.                       Default assumed zero.
