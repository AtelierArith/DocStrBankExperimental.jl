```
simulate_component(rng, c::AbstractComponent, simulation::Simulation)
```

デフォルトでは、`simulate_component`を`(rng, c::Abstractcomponent, design::AbstractDesign)`で呼び出します。これは、カスタムコンポーネントにおいて設計以外のものが必要な場合、例えばオンセット、ノイズ、またはそれに類似するものへの依存関係が必要な場合に「フック」を提供するためだけに存在します。
