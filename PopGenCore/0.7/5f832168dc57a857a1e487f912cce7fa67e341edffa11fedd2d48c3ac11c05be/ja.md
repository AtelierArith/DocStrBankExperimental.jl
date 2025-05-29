```
genepop(data::PopData; filename::String = "output.gen", digits::Int = 3, format::String = "vertical", miss::Int = 0)
```

`PopData`オブジェクトをGenepop形式のファイルに書き込みます。

  * `data`: Genepopファイルに変換したい`PopData`オブジェクト

### キーワード引数

  * `filename`: 出力ファイル名の`String`
  * `digits` : 各アレルをフォーマットする桁数を示す`Integer`（例: `(1, 2)` => `001002` for `digits = 3`）
  * `format` : ロキをフォーマットするかどうかを示す`String`

      * 縦に（`"v"`または`"vertical"`）
      * 横に（`"h"`、または`"horizontal"`）
      * Genepopの距離による隔離（`"ibd"`）で、各サンプルは長さ/緯度データが前に付加された集団
  * `miss` : 欠損値の書き方を示す`Integer`

      * `0` : `digits × ploidy`に等しいゼロの数で表される遺伝型として`000000`（デフォルト）
      * `-9` : 単一の値`-9`として

## 例

```julia
cats = @nancycats;
fewer_cats = omit(cats, name = samplenames(cats)[1:10]);
genepop(fewer_cats, filename = "filtered_nancycats.gen", digits = 3, format = "h")
```
