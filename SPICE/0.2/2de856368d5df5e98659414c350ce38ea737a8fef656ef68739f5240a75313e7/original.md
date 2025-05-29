```
prop2b(gm, pvinit, dt)
```

Given a central mass and the state of massless body at time `t_0`, this routine determines the state as predicted by a two-body force model at time `t_0 + dt`.

### Arguments

  * `gm`: Gravity of the central mass.
  * `pvinit`: Initial state from which to propagate a state.
  * `dt`: Time offset from initial state to propagate to.

### Output

Returns the propagated state.

### References

  * [NAIF Documentation](https://naif.jpl.nasa.gov/pub/naif/toolkit_docs/C/cspice/prop2b_c.html)
