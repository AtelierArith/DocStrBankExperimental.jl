```
KmerFrequencySpectra{1}(freqs::Vector{MerCount{M}}, min_count::Integer = 0) where {M<:AbstractMer}
```

1次元のk-mer頻度スペクトルを、k-merカウントのベクターから構築し、`min_count`を満たさないk-merカウントは除外します。
