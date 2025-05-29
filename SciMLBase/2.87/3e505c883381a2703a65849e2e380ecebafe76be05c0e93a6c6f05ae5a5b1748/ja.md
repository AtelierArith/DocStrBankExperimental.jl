```julia
struct EnsembleSerial <: SciMLBase.BasicEnsembleAlgorithm
```

基本的なアンサンブルソルバーで、並列処理を使用せず、問題を直列で実行します。
