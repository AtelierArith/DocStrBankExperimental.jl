```
extract(self::Union{RheoTimeData,RheoFreqData}, type::Union{TimeDataType,FreqDataType,Integer})
```

Extract specific fields form `RheoTimeData` or `RheoFreqData`.

Deprecated - prefer to use the functions `onlytime`, `onlystrain`, `onlystress`, and `onlyfreq`.

Extract can copy one or more fields from a given `RheoXData` variable into a new `RheoXData` one. The fields that are copied are identified by the specified type of data. If self is a `RheoTimeData`, the type that can be extracted is `time_only` (or `0`), `stress_only` (or `1`), `strain_only` (or `2`). Note that `strain_and_stress` (or `3`) is not allowed. If self is a `RheoFreqData`, the type that can be extracted is `freq_only` (or `0`).
