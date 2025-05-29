```
PruningSat(sat::Sat; factor=0.9)
```

satに基づいて近似的な類似性検索インデックスを作成し、積極的なプルーニングを行います。これは論文 *A probabilistic spell for the curse of dimensionality* (Chavez and Navarro, 2001) から適応されたものです。自動調整をサポートしており、[`optimize!`](@ref)を使用できます。
