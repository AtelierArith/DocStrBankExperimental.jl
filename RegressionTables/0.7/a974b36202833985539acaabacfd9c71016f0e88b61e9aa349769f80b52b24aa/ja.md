`FStatIVPValue`はIV回帰の第一段階F統計量のp値です。StatsAPI.jlパッケージはこれに関する関数を提供していないため、各パッケージ拡張が関連情報を提供する必要があります。ラベルはデフォルトで次のようになります：

  * `AbstractAscii`の場合は「First-stage p value」
  * `AbstractLatex`の場合は「First-stage $p$ value」
  * `AbstractHtml`の場合は「First-stage <i>p</i> value」
