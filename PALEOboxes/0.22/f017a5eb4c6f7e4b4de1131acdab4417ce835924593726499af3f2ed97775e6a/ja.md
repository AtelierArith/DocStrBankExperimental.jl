```
VariableAggregator(vars, cellranges, modeldata, arrays_idx) -> VariableAggregator
```

複数のVariableDomainsをフラットなリスト（連続したVector）に集約します。

`vars`の変数のコレクションに対して、対応する`cellranges`からのインデックスを持つ`VariableAggregator`を作成します。`modeldata`内のデータ配列に対して`arrays_idx`を使用します。

`cellranges`には、全体のDomainを示すために`nothing`エントリが含まれる場合があります。

これは、状態変数、導関数などを集約して、一般的なODE/DAEなどのソルバーへのインターフェースを実装するために主に便利です。

値は[`copyto!`](@ref)を使用してVectorにコピーできます。
