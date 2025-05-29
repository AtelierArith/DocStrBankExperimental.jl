```
function infiltration_capacity(
    Y::ClimaCore.Fields.FieldVector,
    p::NamedTuple,
)
```

土壌の特性、湿度レベル、および池の高さに基づいて土壌の浸透能力を計算する関数。

正の値は土壌への浸透を意味するように定義されています。
