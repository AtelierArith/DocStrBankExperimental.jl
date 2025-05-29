```
SimulatorInferenceSolution{algType,probType,storageType}
```

`SimulatorInferenceProblem`の解のための汎用コンテナ。`result`の型はメソッドに依存し、一般的には推論アルゴリズムの最終状態または生成物（例：事後サンプル）に対応する必要があります。フィールド`output`は`SimulationData`のインスタンスである必要があります。
