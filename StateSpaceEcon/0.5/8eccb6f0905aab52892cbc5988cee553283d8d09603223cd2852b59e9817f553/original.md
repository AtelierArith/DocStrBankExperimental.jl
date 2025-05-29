```
stoch_simulate(model, plan, baseline, shocks; control, ...)
```

Run multiple simulations with the given shocks centered about the given control (steady state by default).

The baseline should span the plan range and must be given in levels ( i.e., option deviation=true is not implemented)

The shocks can be given as a collection of random realizations, where each realization could be an MVTSeries or a Workspace. Only the shocks should be provided.

All shock names must be exogenous in the given plan over the range of the given data. The data in `control` is taken as anticipated and the stochastic realizations are taken as unanticipated and the same plan is used for both components.

Currently only the case of `solver=stackedtime` is implemented.
