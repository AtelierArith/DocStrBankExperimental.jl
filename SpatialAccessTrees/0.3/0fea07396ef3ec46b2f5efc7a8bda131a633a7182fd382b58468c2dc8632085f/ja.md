```
BeamSearchSat(sat::Sat; bsize=8, Δ=1f0)
```

satに基づいて近似的な類似性検索インデックスを作成し、積極的なプルーニングを行います。これは論文 *A probabilistic spell for the curse of dimensionality* (Chavez and Navarro, 2001) から適応されたものです。 [`optimize!`](@ref) を介した自動調整をサポートしています。
