```
spectra(freqs::Vector{MerCount{M}}, min_count::Integer) where {M<:AbstractMer}
```

kmerのカウントのベクトルから、`min_count`を満たさないkmerカウントを除外して、1次元のkmer頻度スペクトルを構築します。
