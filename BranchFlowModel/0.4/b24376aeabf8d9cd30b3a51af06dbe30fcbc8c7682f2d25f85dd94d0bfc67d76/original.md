```
add_linear_variables(m, net::Network{SinglePhase})
```

Add variables for the single-phase, linear model:

  * `Pij` and `Qij` for all `edges(net)`
  * `p0` and `q0` slack bus power
