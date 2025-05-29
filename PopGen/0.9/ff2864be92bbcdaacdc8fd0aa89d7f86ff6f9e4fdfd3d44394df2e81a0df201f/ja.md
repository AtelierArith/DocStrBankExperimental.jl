```
heterozygosity(data::PopData; by::Union{Symbol,String} = "locus")
```

`PopData`オブジェクトにおける観察されたヘテロ接合性と期待されるヘテロ接合性を計算します。遺伝子座に対して、ヘテロ接合性はNei方式で計算され、ヘテロ接合性は各集団ごとの遺伝子座ごとのヘテロ接合性の平均として計算されます。

### モード

  * `"locus"` : 遺伝子座ごとのヘテロ接合性（デフォルト）
  * `"sample"` : 個体/サンプルごとのヘテロ接合性
  * `"population"`: 集団ごとのヘテロ接合性

## 例

heterozygosity(@nancycats, by = "population" ) ```
