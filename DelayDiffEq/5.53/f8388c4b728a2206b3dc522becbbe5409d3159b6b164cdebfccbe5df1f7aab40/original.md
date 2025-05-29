```
reinit!(integrator::DDEIntegrator[, u0 = integrator.sol.prob.u0;
        t0 = integrator.sol.prob.tspan[1],
        tf = integrator.sol.prob.tspan[2],
        erase_sol = true,
        kwargs...])
```

Reinitialize `integrator` with (optionally) different initial state `u0`, different integration interval from `t0` to `tf`, and erased solution if `erase_sol = true`.
