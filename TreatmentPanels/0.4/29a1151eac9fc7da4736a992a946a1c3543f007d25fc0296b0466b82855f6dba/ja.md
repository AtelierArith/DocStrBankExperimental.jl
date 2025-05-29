```
BalancedPanel{TreatmentType}
```

すべての N 治療ユニットが同じ T 期間観察される TreatmentPanel。

このオブジェクトは、すべての結果および共変量データを含む `DataFrame` から構築されます。コンストラクタには、`DataFrame` のどの列が対象と時間期間の識別子を保持しているか、ならびに治療のタイミングに関する情報を渡す必要があります。治療は、治療されたユニットを特定する `String` または `Symbol` の `Pair` と、治療期間を特定する `Date` または `Int` 値として指定されます。治療に終了点がある場合、治療期間は、治療の最初と最後の期間を示す `Date` または `Int` の `Tuple` として指定されます。個々のユニットに複数の治療期間がある場合、これらは治療ユニット識別子とタイミングのベクトルの `Pair{Union{String, Symbol}, Vector{Union{Int, Date}}}` として指定されます。最後に、単一の連続的な治療、単一の周期的な治療、および複数の期間の治療は、複数の治療ユニットに一般化できます。以下の表は、サポートされている治療パターンのタイプの概要を提供します。

|            |                      開始点のみ |                                 開始点と終了点 |                                       複数の開始点と終了点 |
| ----------:| --------------------------:| ---------------------------------------:| ------------------------------------------------:|
| **1 ユニット** |         Pair{String, Date} |         Pair{String, Tuple{Date, Date}} |         Pair{String}, Vector{Tuple{Date, Date}}} |
| **複数ユニット** | Vector{Pair{String, Date}} | Vector{Pair{String, Tuple{Date, Date}}} | Vector{Pair{String}, Vector{Tuple{Date, Date}}}} |
