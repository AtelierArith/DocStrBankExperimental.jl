```
default_logger()
```

サポートされている機械学習トラッキングプラットフォーム、例えば [MLflow](https://mlflow.org/docs/latest/index.html) で使用するためのデフォルトロガーの現在の値を返します。

デフォルトロガーは、[`evaluate!`](@ref) および [`evaluate`](@ref) への呼び出し、ならびに `TunedModel` と `IteratedModel` のコンストラクタで使用されますが、`logger` キーワードが明示的に指定されていない限りです。

!!! note
    MLJ v0.20.7（および MLJBase 1.5）以前では、デフォルトロガーは常に `nothing` でした。


MLJBase が最初にロードされると、デフォルトロガーは `nothing` です。
