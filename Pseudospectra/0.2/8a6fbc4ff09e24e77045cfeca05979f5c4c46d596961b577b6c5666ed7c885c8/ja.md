```
spectralportrait(A::AbstractMatrix; npts=100) => Plots object
```

行列 `A` の擬似スペクトルを計算し、スペクトルポートレートとして表示します。

擬似スペクトルは、スペクトルの近傍を含む複素平面の `npts` x `npts` のグリッド上で計算されます。等高線レベルは `log10(ϵ)` であり、ここで `ϵ` は逆レゾルベントノルムです。これは単純なケースのための便利なラッパーです。より複雑なインターフェースについては、Pseudospectra パッケージのドキュメントを参照してください。
