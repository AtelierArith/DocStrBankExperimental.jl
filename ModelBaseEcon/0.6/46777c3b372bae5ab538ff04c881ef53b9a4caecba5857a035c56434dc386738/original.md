```
issssolved(sstate::SteadyStateData)
```

Return `true` if the steady state has been solved, or `false` otherwise.

!!! note
    This function only checks that the steady state is marked as solved. It does not verify that the stored steady state values actually satisfy the steady state system of equations. Use `check_sstate` from StateSpaceEcon for that.

