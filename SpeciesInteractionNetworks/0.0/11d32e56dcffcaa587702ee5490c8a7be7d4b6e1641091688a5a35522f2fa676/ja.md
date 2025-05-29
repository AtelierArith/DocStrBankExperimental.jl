```
BetaDivComponent
```

[`betadiversity`](@ref) メソッドはすべて、測定すべきコンポーネントを決定するために `BetaDivComponent` のサブタイプを最初の引数として使用します。

すべてのパーティションは [Koleff2003Measuring](@citet) アプローチに従い、ベータ多様性は集合の基数に基づいて測定されます。具体的には、すべての [`betadiversity`](@ref) 関数は、`shared`、`left`、`right` という3つのフィールドを持つ名前付きタプルを返します。これらはそれぞれ、両方のネットワークに共通するアイテムの数、最初の引数に特有のアイテムの数、および2番目の引数に特有のアイテムの数を表します。

###### 参考文献

[Koleff2003Measuring](@citet*)
