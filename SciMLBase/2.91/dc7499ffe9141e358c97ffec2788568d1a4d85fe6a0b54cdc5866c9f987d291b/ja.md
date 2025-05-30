```julia
struct EnsembleThreads <: SciMLBase.BasicEnsembleAlgorithm
```

デフォルトです。これはマルチスレッドを使用します。ローカル（単一コンピュータ、共有メモリ）並列処理のみです。小さな問題に対しては最低の並列処理オーバーヘッドです。
