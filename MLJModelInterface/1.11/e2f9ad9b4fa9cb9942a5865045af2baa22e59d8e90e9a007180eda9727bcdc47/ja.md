```
MLJModelInterface.fit(model, verbosity, data...) -> fitresult, cache, report
```

すべてのモデルは `fit` メソッドを実装する必要があります。ここで `data` は、ユーザーが提供したデータに対する `reformat` の出力、またはその再サンプリングのいずれかです。`reformat` のフォールバックは、ユーザーが提供したデータ（例えば、テーブル）を返します。
