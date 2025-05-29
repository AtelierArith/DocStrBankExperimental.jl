```
colrec
```

`colrec` データセットは、スロベニアからの相対生存データセットの例を提供し、`RateTables.jl` パッケージの `slopop` レートテーブルとペアにする必要があります。以下の列が含まれています：

  * `time`、日数：診断からのフォローアップ時間、
  * `status`、ブール値：観察された死亡 (1) または検閲 (0)、
  * `age`、日数：診断時の年齢、
  * `year`、0000-00-00 からの日数：診断日、
  * `sex`、`:male` または `:female`、
  * `stage`、癌のステージ、1、2、3 または 99 (不明) である可能性があります、
  * `site`、癌の部位、`:rectum` または `:colon` である可能性があります。

5971 人の患者が 1994 年から 2000 年の間に大腸癌または直腸癌と診断されました。データセットの元のソースは [`relsurv` R パッケージ](https://CRAN.R-project.org/package=relsurv) です。データはスロベニア癌登録所によって提供されました。収集された元のデータは、プライバシーの目的と法的理由のために若干修正されました。このデータの摂動のため、日付や年齢は厳密にその実際の元の値に対応していません。このデータセットはしたがって、教育的および方法論的な例として提供されており、医療研究の目的で使用すべきではありません。

参考文献：

  * [Pavlik2018](@cite) Pohar Perme, Maja と Pavlic, Klemen (2018). R パッケージ relsurv を用いた非パラメトリック相対生存分析. Journal of Statistical Software
  * [Zadnik2012](@cite) Zadnik V, Primic Žakelj M, Krajc M (2012). スロベニアにおける癌の負担と他の欧州諸国との比較. Zdravniški Vestnik
  * [Zadnik2016](@cite) Zadnik V, Žagar T, Primic Žakelj M (2016). 癌患者の生存：標準的な計算方法とその解釈に関するいくつかの考慮事項. Zdravstveno Varstvo
