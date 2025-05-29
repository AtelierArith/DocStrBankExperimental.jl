```
function simulate_magnetization(sequence, parameters)
```

計算リソースを指定せずに磁化をシミュレートするための便利な関数です。この関数は、`sequence` と `parameters` のタイプに基づいて適切なリソースを自動的に選択します。フォールバックケースは、マルチスレッドCPU計算を使用することです。
