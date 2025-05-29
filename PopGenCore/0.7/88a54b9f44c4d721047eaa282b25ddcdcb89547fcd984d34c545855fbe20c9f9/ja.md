```
baypass(data::PopData; filename::Union{String, Nothing} = nothing)
```

`PopData`オブジェクトをBaypass形式の行列に変換します。ソフトウェアに必要な入力形式は二対立遺伝子データです。デフォルトでは、Baypass形式の行列のみを返します。行列を書き込むファイルを指定するには、キーワード引数`filename`を使用します。この関数は**Baypass分析を実行するものではなく**、そのために必要な入力行列を作成します。

行列の仕様は次のとおりです：

  * 行 = ロキ

      * 各行は異なるロキです
  * 列 = 各集団のアレル数

      * 各列のペアは、集団のアレル数（2つのアレル、2つの列）に対応します
      * 結果として、2 × n_populations列が必要です
      * 例：行1、列1:2は、集団1のロキ1のアレル数です

Baypass情報: http://www1.montpellier.inra.fr/CBGP/software/baypass/ ```
