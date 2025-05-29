```
AbstractHiddenMarkovModel
```

任意の出力を持つ隠れマルコフモデルのインターフェース。

# 必要なメソッド

  * [`nb_states(hmm, par)`](@ref)
  * [`initial_distribution(hmm, par)`](@ref)
  * [`transition_matrix(hmm, par)`](@ref)
  * [`emission_distribution(hmm, s, par)`](@ref)

# オプションのメソッド

  * [`log_initial_distribution(hmm, par)`](@ref)
  * [`log_transition_matrix(hmm, par)`](@ref)

# 互換性のあるもの

  * [`rand(rng, hmm, T, par)`](@ref)
  * [`logdensityof(hmm, obs_sequence, par; safe)`](@ref)
  * [`infer_current_state(hmm, obs_sequence, par; safe)`](@ref)
