```julia
struct EnsembleSplitThreads <: SciMLBase.BasicEnsembleAlgorithm
```

分散コンピューティングとスレッドの混合です。これの最適なバージョンは、コンピュータの各ノードにプロセスを持ち、各システムでマルチスレッドを行うことです。しかし、このアンサンブルは、Juliaの分散プロセスによって提供されるノードセットアップを単純に使用しますので、このアンサンブルを使用する前にこのようにプロセスを設定することをお勧めします。詳細については、Juliaの分散ドキュメントを参照してください。
