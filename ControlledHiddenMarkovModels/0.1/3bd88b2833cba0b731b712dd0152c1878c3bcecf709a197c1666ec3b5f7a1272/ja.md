```
AbstractControlledHiddenMarkovModel
```

任意の出力と外的制御変数を持つ隠れマルコフモデルのインターフェース。

# 必要なメソッド

  * [`nb_states(hmm, par)`](@ref)
  * [`initial_distribution(hmm, par)`](@ref)
  * [`transition_matrix(hmm, control, par)`](@ref)
  * [`transition_matrix!(P, hmm, control, par)`](@ref)
  * [`emission_parameters(hmm, control, par)`](@ref)
  * [`emission_parameters!(θ, hmm, control, par)`](@ref)
  * [`emission_distribution(hmm, s, θ)`](@ref)

# オプションのメソッド

  * [`log_initial_distribution(hmm, par)`](@ref)
  * [`log_transition_matrix(hmm, control, par)`](@ref)
  * [`log_transition_matrix!(logP, hmm, control, par)`](@ref)

# 互換性のあるもの

  * [`rand(rng, hmm, control_sequence, par)`](@ref)
  * [`logdensityof(hmm, obs_sequence, control_sequence, par; safe)`](@ref)
  * [`infer_current_state(hmm, obs_sequence, control_sequence, par; safe)`](@ref)
