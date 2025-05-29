```
ParsedReactionNetwork(rn::ReactionSystem; u0 = nothing, p = nothing, varstonames = nothing, groupstosyms = nothing)
```

解析された反応ネットワークとその関連メタデータを格納するためのコンテナです。

# フィールド

  * `rn`、Catalystの`ReactionSystem`。**注意** このシステムはデフォルトでは*完全*とはマークされていません（システムの完全性についての議論は[こちらのCatalystドキュメント](https://catalyst.sciml.ai/)を参照してください）。
  * `u0`、初期条件の記号変数を数値と/または記号式にマッピングする`Dict`。
  * `p`、パラメータの記号変数を数値と/または記号式にマッピングする`Dict`。
  * `varstonames`、生成された`ReactionSystem`で使用される種の内部記号変数を、.netファイルの名前から生成された`String`にマッピングする`Dict`。これは、BioNetGenが非常に長い種名を生成する可能性があり、`Catalyst`と一緒に使用すると不正な種名につながる文字を含むため、必要です。
  * `groupstosyms`、BioNetGenファイルで定義された任意のグループの名前を表す`String`を、そのグループに関連する`ModelingToolkit`の記号的観測量を表す対応する記号変数にマッピングする`Dict`。
