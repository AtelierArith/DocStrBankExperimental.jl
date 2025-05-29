```
state = initialize_particle_filter(model::GenerativeFunction, model_args::Tuple,
    observations::ChoiceMap, num_particles::Int)
```

初期の潜在状態のためのデフォルト提案を使用して、粒子フィルタの状態を初期化します。
