`FStatPValue`は回帰のF統計量のp値です。StatsAPI.jlパッケージはこれに関する関数を提供していないため、各パッケージ拡張が関連情報を提供する必要があります。ラベルはデフォルトで次のようになります：

  * `AbstractAscii`の場合は「F p value」
  * `AbstractLatex`の場合は「$F$ $p$ value」
  * `AbstractHtml`の場合は「<i>F</i> <i>p</i> value」
