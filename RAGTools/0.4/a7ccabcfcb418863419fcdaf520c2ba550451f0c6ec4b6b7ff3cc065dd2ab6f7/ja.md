```
AdvancedGenerator <: AbstractGenerator
```

`generate!` のデフォルト実装です。これは単にコンテキストスニペットを列挙し、`aigenerate` を実行します（洗練はありません）。

デフォルトの `contexter`、`answerer`、`refiner`、および `postprocessor` として `ContextEnumerator`、`SimpleAnswerer`、`SimpleRefiner`、および `NoPostprocessor` を使用します。
