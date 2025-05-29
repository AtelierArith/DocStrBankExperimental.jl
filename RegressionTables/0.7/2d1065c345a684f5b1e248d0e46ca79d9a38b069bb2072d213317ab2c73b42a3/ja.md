`FStatIV`はIV回帰の第一段階F統計量です。StatsAPI.jlパッケージはこれに関する関数を提供していないため、各パッケージ拡張が関連情報を提供する必要があります。ラベルはデフォルトで次のようになります：

  * `AbstractAscii`の場合は「第一段階F統計量」
  * `AbstractLatex`の場合は「第一段階 $F$ 統計量」
  * `AbstractHtml`の場合は「第一段階 <i>F</i> 統計量」
