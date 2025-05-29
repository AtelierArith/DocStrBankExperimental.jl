```
ContinuousSystem(sysid, A, B, C, D, inputid [, Rc, Qc])
```

Create a continuous-time linear system

```
u(t) --> sys --> y(t)
         x(t)
```

The state initially has mean value `E(x) = 0` and covariance `V(x) = 0`.

## Arguments:

  * `sysid`:          A unique positive `Integer` identifier for this system (pick any). Used when referred to from other systems.
  * `[A, B, C, D]`:   A strictly proper, delay-free continuous-time LTI system in state-space form.
  * `inputid`:        A vector of input system identifiers.                    The outputs of the corresponding systems will be used as inputs to this system.                   The number of inputs in this system must equal the total number of outputs in the input systems.                   An empty vector (or zero) indicates that the system inputs are unconnected.
  * `Rc`:             (OPTIONAL) The continuous state or input noise intensity matrix.                    The noise vector is assumed to have the same size as x (for state-space systems).                   Default assumed zero.
  * `Qc`:             (OPTIONAL) The continuous cost function is `E(Integral [x(t); u(t)]' * Qc * [x(t); u(t)] dt)` (for state-space systems).                   Default assumed zero.
