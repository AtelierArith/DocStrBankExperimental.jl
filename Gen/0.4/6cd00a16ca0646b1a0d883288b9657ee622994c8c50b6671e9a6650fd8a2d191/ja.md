```
did_resample::Bool = maybe_resample!(state::ParticleFilterState;
    ess_threshold::Float64=length(state.traces)/2, verbose=false)
```

与えられた閾値未満の場合、効果的サンプルサイズに基づいて再サンプリングステップを実行します。再サンプリングが行われた場合は `true` を返し、そうでない場合は `false` を返します。
