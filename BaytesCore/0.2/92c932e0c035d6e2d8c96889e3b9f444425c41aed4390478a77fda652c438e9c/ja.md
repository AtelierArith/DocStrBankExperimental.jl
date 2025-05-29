```julia
abstract type AbstractDiagnostics
```

アルゴリズム診断のための抽象スーパタイプ。`AbstractAlgorithm`が実行された後、新しいモデルパラメータと`AbstractDiagnostics`を`AbstractAlgorithm`から返します。
