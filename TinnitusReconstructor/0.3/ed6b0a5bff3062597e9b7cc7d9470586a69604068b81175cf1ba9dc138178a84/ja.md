```
generate_stimuli_matrix(s::SG, n_trials::I) where {SG<:Stimgen, I<:Integer}
```

`stimgen`タイプの仕様に基づいて`n_trials`の刺激を生成します。

`stimuli_matrix`、`Fs`、`spect_matrix`、`binned_repr_matrix`を返します。`binned_repr_matrix` = nothing if s >: BinnedStimgen.
