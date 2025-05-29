`R2Within`は固定効果回帰の内部R二乗です。StatsAPI.jlパッケージはこれに関する関数を提供していないため、各パッケージ拡張が関連情報を提供する必要があります。ラベルはデフォルトで次のようになります：

  * `AbstractAscii`の場合は「Within R2」
  * `AbstractLatex`の場合は「Within $R^2$」
  * `AbstractHtml`の場合は「Within <i>R</i><sup>2</sup>」
