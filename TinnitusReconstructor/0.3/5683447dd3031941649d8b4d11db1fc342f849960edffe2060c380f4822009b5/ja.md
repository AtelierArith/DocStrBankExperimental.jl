```
generate_stimuli_matrix(s::BS, n_trials::I) where {BS<:BinnedStimgen, I<:Integer}
```

指定されたstimgenタイプに基づいて`n_trials`の刺激を生成します。

`stimuli_matrix`、`Fs`、`spect_matrix`、`binned_repr_matrix`を返します。
