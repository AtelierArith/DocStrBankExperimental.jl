```
state = initialize_particle_filter(model::GenerativeFunction, model_args::Tuple,
    observations::ChoiceMap, proposal::GenerativeFunction, proposal_args::Tuple,
    num_particles::Int)
```

カスタム提案を使用して初期潜在状態の粒子フィルタの状態を初期化します。
