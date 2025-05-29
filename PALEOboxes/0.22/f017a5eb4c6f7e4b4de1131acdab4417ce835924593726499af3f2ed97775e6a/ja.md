```
VariableAggregator(vars, cellranges, modeldata, arrays_idx) -> VariableAggregator
```

複数の VariableDomains をフラットなリスト（連続したベクター）に集約します。

`vars` の変数のコレクションに対して、対応する `cellranges` からのインデックスを持つ `VariableAggregator` を作成し、`modeldata` のデータ配列に `arrays_idx` を使用します。

`cellranges` には、全体のドメインを示すために `nothing` エントリを含めることができます。

これは、状態変数、導関数などを集約して、一般的な ODE/DAE などのソルバーへのインターフェースを実装するために主に便利です。

値は [`copyto!`](@ref) を使用してベクターにコピーすることができます。
