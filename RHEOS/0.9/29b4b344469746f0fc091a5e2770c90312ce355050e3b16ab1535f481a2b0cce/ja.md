```
extract(self::Union{RheoTimeData,RheoFreqData}, type::Union{TimeDataType,FreqDataType,Integer})
```

`RheoTimeData` または `RheoFreqData` から特定のフィールドを抽出します。

非推奨 - `onlytime`、`onlystrain`、`onlystress`、および `onlyfreq` 関数の使用を推奨します。

Extract は、指定された `RheoXData` 変数から新しい `RheoXData` 変数に1つ以上のフィールドをコピーできます。コピーされるフィールドは、指定されたデータのタイプによって特定されます。self が `RheoTimeData` の場合、抽出できるタイプは `time_only`（または `0`）、`stress_only`（または `1`）、`strain_only`（または `2`）です。`strain_and_stress`（または `3`）は許可されていないことに注意してください。self が `RheoFreqData` の場合、抽出できるタイプは `freq_only`（または `0`）です。
