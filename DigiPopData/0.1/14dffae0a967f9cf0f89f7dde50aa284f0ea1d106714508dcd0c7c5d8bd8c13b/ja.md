```
parse_metric_bindings(df::DataFrame) -> Vector{MetricBinding}
```

`DataFrame`を解析してメトリックバインディング定義を取得し、[`MetricBinding`](@ref)オブジェクトのベクターを返します。

DataFrameは以下の列を含む必要があります：

  * `id`: メトリックバインディングの一意の識別子。
  * `scenario`: メトリックバインディングが適用されるシナリオ。
  * `endpoint`: メトリックバインディングに関連付けられた観測可能なエンドポイント。
  * `active`: （オプション）メトリックバインディングがアクティブかどうかを示すブール値（デフォルトは`true`）。
  * `metric.type`: メトリックのタイプ（例："mean", "category"など）。
  * `metric.<parameter>`: メトリックのタイプに応じた追加のパラメータ。

この関数は`PARSERS`辞書を使用してメトリックタイプに適したパーサーを見つけます。関数はDataFrameの各行を反復処理し、関連情報を抽出して`MetricBinding`オブジェクトを作成します。
