```
sosbound_γ(s::StateDepDiscreteSwitchedLinearSystem, d)
```

Compute minimum value of $γ$ for which the sum-of-squares program is feasible.

# Keywords

  * `optimizer=...`: choose an SDP solver. The default solver is CSDP.
  * `tol=...`: set tolerance. The default is `tol=1e-5`.
  * `verbose=...`: set level of detail reported during calculation process. The default is

`verbose=0`.

  * `initstep=...`: set initial step size. The default value is `initstep=1.1`.
