```
plan_edf_to_onda_samples(edf::EDF.File;
                         labels=STANDARD_LABELS,
                         units=STANDARD_UNITS,
                         extra_onda_signal_groupby=())
```

`EDF.File`をOnda Samplesに変換する計画を立てます。これは、ファイルに含まれる各個別信号に`plan_edf_to_onda_samples`を適用し、`edf_signal_index`を追加の列として保存します。

結果として得られた行は、[`plan_edf_to_onda_samples_groups`](@ref)に渡され、`:sensor_type`、`:sample_unit`、`:sample_rate`列および`extra_onda_signal_groupby`で指定された追加の列に従ってグループ化されます。各グループには、最初の後の`n`回目の`sensor_type`に対して数値サフィックス`_n`を付けた`sensor_label`が生成されます。

結果の計画はテーブルとして返されます。信号データは実際にはEDFファイルから読み込まれません。この計画を実行して`Onda.Samples`を生成するには、[`edf_to_onda_samples`](@ref)を使用します。各行のEDF信号のインデックス（`EDF.Signal`でない信号、例えば注釈チャネルをフィルタリングした後）が`:edf_signal_index`列に保存され、行は`:sensor_label`の順序で、次に`:edf_signal_index`でソートされます。
