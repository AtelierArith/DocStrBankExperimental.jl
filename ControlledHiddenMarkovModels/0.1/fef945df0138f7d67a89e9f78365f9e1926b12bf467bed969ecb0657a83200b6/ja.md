```
HiddenMarkovModel{R1,R2,D}
```

[`AbstractHMM`](@ref) の具体的なサブタイプで、状態と観測パラメータを直接保存します。

# フィールド

  * `p0::Vector{R1}`
  * `P::Matrix{R2}`
  * `emissions::Vector{D}`

# 互換性があるもの

  *   * [`baum_welch_multiple_sequences(obs_sequences, hmm_init, par; kwargs...)`](@ref)
  *   * [`baum_welch(obs_sequence, hmm_init, par; kwargs...)`](@ref)
