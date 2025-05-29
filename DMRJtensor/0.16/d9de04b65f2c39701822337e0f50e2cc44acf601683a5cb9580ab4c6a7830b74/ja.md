compressMPO!(W[,sweeps=,cutoff=,deltam=,minsweep=,nozeros=])

MPO (`W`; または複数の `M`) を SVD 圧縮を用いて `sweeps` 回圧縮し、`cutoff` を SVD に適用し、`deltam` を結合次元圧縮のターゲットとして、`nozeros` をデフォルトで true に設定して SVD のすべてのゼロを排除します。
