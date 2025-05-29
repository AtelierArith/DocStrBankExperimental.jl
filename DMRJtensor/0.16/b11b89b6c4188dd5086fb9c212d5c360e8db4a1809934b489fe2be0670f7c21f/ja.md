compressMPO!(W[,sweeps=,cutoff=,deltam=,minsweep=,nozeros=])

MPOの配列（`W`）を、`sweeps`スイープでSVD圧縮を用いて並列に圧縮します。`cutoff`はSVDに適用され、`deltam`は結合次元圧縮のターゲット、`nozeros`はデフォルトでtrueに設定され、SVD内のすべてのゼロを排除します。
