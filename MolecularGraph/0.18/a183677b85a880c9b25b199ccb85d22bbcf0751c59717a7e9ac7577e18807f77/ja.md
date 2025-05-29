```
QueryTruthTable(fml::Function, props::Vector{QueryLiteral}) -> QueryTruthTable
```

クエリの一致と包含のための真理値表評価器。

これは `generate_truthtable` を使用して生成されることが期待されています。プロパティは一意であり、手動で QueryTruthTable コンストラクタがテストのために呼び出される場合はソートされている必要があります。

  * function: 各プロパティ変数に対応するサイズ `length(props)` のベクターを受け取り、真または偽を返す関数。
  * props: QueryLiteral ベクター。
