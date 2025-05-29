`macro makeBaseMeasure(quantityName, unitName, unitSymbol::String, isAffine=false)`

新しい基準測定を作成します。これは既存の単位とは関係がありません。例えば、`@makeBaseMeasure Length Meter "m"` の場合：

  * `quantityName` は測定の名前で、上記の 'Length' です。
  * `unitName` はその単位を持つ測定を作成するために使用される単位の名前で、上記の 'Meter' です。
  * `unitSymbol` は単位名の略称で、測定のすべての文字列表現で使用されます。
  * `isAffine` は通常 false で、true の場合はこの単位および派生単位に対して +-/* 演算が追加されず、手動で追加する必要があります。

このマクロは、現在のスコープに `AbstractLength <: AbstractMeasure` と `Meter()` を導入します。

マクロによって作成された測定には次のフィールドがあります：

  * `value::Number` 測定の生の値
  * `toBase::Number` 基準測定の場合は 1
  * `unit::String` 表示される単位

基準単位での測定値を浮動小数点数として取得するには、toBaseFloat() を参照してください。
