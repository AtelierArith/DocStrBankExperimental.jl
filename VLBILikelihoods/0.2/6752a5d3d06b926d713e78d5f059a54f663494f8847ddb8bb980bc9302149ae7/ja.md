```
RiceAmplitudeLikelihood(μ, Σ::Union{AbstractVector, Diagonal})
```

平均ベクトル `μ` と対角共分散行列 `Σ` から振幅の尤度を形成します。`Σ` は対角行列または各データポイントの分散を表すベクトルのいずれかです。

!!! note
    これは可視性振幅に対する正しい尤度分布ですが、ガウス近似 `AmplitudeLikelihood` よりも遅くなります。しかし、低SNRデータの場合は、バイアスのない結果を得るために必要です。

