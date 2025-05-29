```
@version FilePlanV4 > PlanV4 begin
    recording::Union{UUID,Missing} = lift(UUID, recording)
    edf_signal_index::Int
    sensor_label::Union{String,Missing}
end
```

Legolasによって生成されたレコードタイプは、1つのEDF信号からOndaチャネルへの変換を表しており、[`PlanV4`](@ref)の列と追加のファイルレベルのコンテキストを含みます：

  * `recording::Union{UUID,Missing}` は、既知であれば録音のUUIDです。
  * `edf_signal_index` は、この行に対応するソース`EDF.File`内の`signals`のインデックスを示します。
  * `sensor_label::AbstractString` は、変換後の対応する出力`Onda.Samples`の一意の識別子を示します。
