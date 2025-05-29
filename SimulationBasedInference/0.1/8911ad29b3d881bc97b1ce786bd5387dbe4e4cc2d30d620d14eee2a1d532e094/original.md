```
SciMLBase.remake(
    forward_prob::SimulatorForwardProblem;
    prob=forward_prob.prob,
    observables=forward_prob.observables,
    config=forward_prob.config,
    copy_observables=true,
    kwargs...
)
```

Rebuilds a `SimulatorForwardProblem` from its individual components. If `copy_observables=true`, then `remake` will `deepcopy` the observables to ensure independence. The default setting is `true`.
