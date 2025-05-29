```
missingdata(data::PopData; by::Union{String, Symbol} = "sample")
```

`PopData`内の欠損した遺伝型情報を取得します。欠損情報に対応するDataFrameを返す操作モードを指定します。

#### モード

  * "sample" - 各個体ごとの欠損ロキの数と割合、およびリストを返します（デフォルト）
  * "population" - 各集団ごとの欠損遺伝型の数と割合を返します
  * "locus" - 各ロキごとの欠損遺伝型の数と割合を返します
  * "locusxpopulation" - 各集団ごとの各ロキの欠損遺伝型の数と割合を返します

### 例:

```
missingdata(@gulfsharks, by = "pop")
```
