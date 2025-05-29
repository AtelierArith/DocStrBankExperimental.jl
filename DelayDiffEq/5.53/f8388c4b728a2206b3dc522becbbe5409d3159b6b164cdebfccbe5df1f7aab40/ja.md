```
reinit!(integrator::DDEIntegrator[, u0 = integrator.sol.prob.u0;
        t0 = integrator.sol.prob.tspan[1],
        tf = integrator.sol.prob.tspan[2],
        erase_sol = true,
        kwargs...])
```

`integrator`を（オプションで）異なる初期状態`u0`、`t0`から`tf`までの異なる積分区間で再初期化し、`erase_sol = true`の場合は解を消去します。
