```
@version FilePlanV3 > PlanV3 begin
    edf_signal_index::Int
    onda_signal_index::Int
end
```

Legolasによって生成されたレコードタイプで、1つのEDF信号からOndaチャネルへの変換を表し、[`PlanV3`](@ref)の列と追加のファイルレベルのコンテキストを含みます：

  * `edf_signal_index`は、この行に対応するソース`EDF.File`内の`signals`のインデックスを示します
  * `onda_signal_index`は、出力`Onda.Samples`のインデックスを示します。

EDFインデックスは実際の`edf.signals`内のインデックスに対応していますが、一部のOndaインデックスは出力でスキップされる可能性があるため、`onda_signal_index`は順序とグループ化を示すためのものです。
