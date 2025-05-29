```
pre_allocate(
    model::BiophysicalModel, sampler::Sampler, datasize::Tuple{Int64,Int64}
)

pre_allocate(
    model::BiophysicalModel, sampler::Tuple{Sampler,Sampler}, datasize::Tuple{Int64,Int64}
)
```

`model`、`sampler`、および `datasize` に基づいて計算結果をキャッシュするためのスペースを割り当てます。`datasize` はデータのサイズ (Nmeas, Nvoxels) です。
