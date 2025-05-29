```
get_energies(k::KernelLabel; W = 0. * I)
```

Get the relevant energies of a kernel label `k` with boundary weighting matrix `W`.

Output energies:

  * `EK = ‖c‖²_k` is the smoothing kernel norm
  * `EInv = ‖GKc‖²` is a norm penalizing invariance
  * `Ebd = ‖Kc‖²_W` is a norm penalizing boundary violation
  * `EL2 = ‖Kc‖²` is the ℓ² norm of the points
