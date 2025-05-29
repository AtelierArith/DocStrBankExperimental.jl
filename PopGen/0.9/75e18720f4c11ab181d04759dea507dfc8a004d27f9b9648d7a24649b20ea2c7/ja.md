```
hwetest(data::PopData; by::String = "locus", correction = "none")
```

各ローカスのHWEのカイ二乗検定を計算し、各ローカスの観察されたおよび期待されるヘテロ接合度、カイ二乗、自由度、p値を返します。`by = "population"`を使用して、各集団ごとにこれを個別に実行します（デフォルト：`by = "locus"`）。`correction =`を使用して、多重検定のためのP値調整方法を指定します。

#### 例

`hwetest(@gulfsharks, correction = "bh")` 

`hwetest(@gulfsharks, by = "population", correction = "bh")` 

### `correction` メソッド（大文字と小文字を区別しない）

  * `"bonferroni"` : ボンフェローニ調整
  * `"holm"` : ホルム調整
  * `"hochberg"` : ホッホバーグ調整
  * `"bh"` : ベンジャミニ-ホッホバーグ調整
  * `"by"` : ベンジャミニ-イェクティエリ調整
  * `"bl"`  : ベンジャミニ-リウ調整
  * `"hommel"` : ホメル調整
  * `"sidak"` : Šidák調整
  * `"forwardstop"` または `"fs"` : フォワードストップ調整
  * `"bc"` : バーバー-カンデス調整
