```
delimited(data::PopData; filename::String, delim::String = ",", digits::Integer = 3, format::String = "wide", miss::Int = 0)
```

PopDataをテキスト区切りファイルに書き込みます。

### キーワード引数

  * `filename`: 出力ファイル名の`String`
  * `digits` : 各アレルをフォーマットする桁数を示す`Integer`（例: `(1, 2)` => `001002` for `digits = 3`）
  * `format` : `"wide"`または`"long"`（別名`"tidy"`）形式で出力するかを示す`String`

      * `wide` : PopGen.jlにインポートするための標準形式CSV
      * `long` : `longitude`および`latitude`列が追加された`loci`テーブル
  * `delim` : ファイルを書き込むために使用する`String`区切り文字
  * `miss` : 欠損値をどのように書き込みたいかのための`Integer`

      * `0` : `digits × ploidy`に等しいゼロの数で表される遺伝子型として`000000`（デフォルト）
      * `-9` : 単一の値`-9`として

### 例

```julia
cats = @nancycats;
fewer_cats = omit(cats, name = samplenames(cats)[1:10]);
delimited(fewer_cats, filename = "filtered_nancycats.gen", digits = 3, format = "wide", delim = " ")
```
