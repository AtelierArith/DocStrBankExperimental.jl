```
devito_model(model, options;dm=nothing)
```

DevitoのためのPython側モデル構造を作成します。

パラメータ

  * `model`: JUDIモデル構造。
  * `options`: JUDIオプション構造。
  * `dm`: 二乗遅延の摂動（オプション）、配列またはPhysicalParameter。
