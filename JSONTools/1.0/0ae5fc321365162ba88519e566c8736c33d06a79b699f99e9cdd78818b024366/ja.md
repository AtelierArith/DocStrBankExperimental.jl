ワイルドカードは、JSONパスで複数のキーやインデックスを一度に一致させるために使用されます。ワイルドカードには4種類あります：

  * `ANY_KEY` - `Dict`内の任意のキーに一致します。
  * `ANY_INDEX` - `Vector`内の任意のインデックスに一致します。
  * `ANY` - `Dict`内の任意のキーまたは`Vector`内のインデックスに一致します。
  * `SKIP_LIST` - パス内の現在の値が`Vector`の場合、すべてのインデックスに一致します。現在の値が`Vector`でない場合、現在の値を1つの要素を持つ結果のタプルにパッキングする以外には効果がありません。

ワイルドカードはデータの読み取りにのみ使用でき、設定には使用できません。
