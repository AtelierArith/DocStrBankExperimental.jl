```
edf_to_onda_samples(edf::EDF.File, plan_table; validate=true, dither_storage=missing)
```

EDFファイルに見つかった信号を、`plan_table`で指定された計画に従って`Onda.Samples`に変換します（例：[`plan_edf_to_onda_samples`](@ref)によって生成されたもの）。[`Vector{ConvertedSamples}`](@ref ConvertedSamples)を返します。実行された計画と`Onda.Samples`をそれぞれ抽出するには、[`get_plan`](@ref)と[`get_samples`](@ref)を使用してください。

入力計画は、同じ`:sensor_label`を持つ行を共通の`Onda.SamplesInfo`に結合するために[`merge_samples_info`](@ref)を使用して変換されます。その後、[`OndaEDF.onda_samples_from_edf_signals`](@ref)を使用して、EDF信号データをグループごとに単一の`Onda.Samples`に結合します。

発生したエラーは`String`（バックトレース付き）として表示され、計画の対応する行の`:error`列に挿入されます。

サンプルは、対応する`:sensor_label`が計画に現れる順序で返されます。計画内の同じ計画`:sensor_label`を持つすべてのEDF信号は、`:edf_signal_index`の順序で単一の`Onda.Samples`に結合されます。マッチできなかった信号、`:sensor_label`が`missing`であるもの、または実行中にエラーを引き起こしたものは返されません。

`validate=true`（デフォルト）である場合、計画は[`FilePlanV4`](@ref)スキーマおよび`EDF.File`内の信号ヘッダーに対して検証されます。

`dither_storage=missing`（デフォルト）である場合、ditherストレージは`Onda.encode`のドキュメントに指定されたように自動的に割り当てられます。`dither_storage=nothing`は、ディザリングを無効にします。

!!! warning
    返されたサンプルは整数エンコードされています。これらのサンプルがシリアライズされる場合（例：`Onda.store!`を介して）、これは問題ではありませんが、サンプルがメモリ内で即座に分析される場合は、`Onda.decode`を呼び出して、時系列の電圧を回復する必要があります。

