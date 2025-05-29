```
initialize(::Type{<:MaternCorrelationStructure}, data::IDFdata)
```

データに適応したMaternCorrelationStructureのパラメータベクトルを初期化します。初期化は、各ペアの期間に関連するKendallのタウ（相関の尺度）に相関関数をフィットさせることによって行われます。
