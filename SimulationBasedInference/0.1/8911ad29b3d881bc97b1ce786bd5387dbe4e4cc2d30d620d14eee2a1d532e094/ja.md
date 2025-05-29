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

`SimulatorForwardProblem`をその個々のコンポーネントから再構築します。`copy_observables=true`の場合、`remake`は観測量を`deepcopy`して独立性を確保します。デフォルト設定は`true`です。
