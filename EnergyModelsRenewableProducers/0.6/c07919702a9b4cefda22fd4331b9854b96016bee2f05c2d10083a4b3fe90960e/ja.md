```
ScheduleConstraint{T} <: Data where {T<:AbstractScheduleType}
```

追加できる制約 `Data` として。 `T <: AbstractScheduleType` は制約の型を示します。

## フィールド

  * **`resource::{Union{<:Resource, Nothing}}`** は、ノードが複数のリソースを入力/出力として持つことができる場合に、制約が適用されるリソースの型です。
  * **`value::TimeProfile`** は、制約の値であり、違反してはいけない制限です。
  * **`flag::TimeProfile`** は、制約がアクティブかどうかを示すブール値です。
  * **`penalty::TimeProfile`** は、制約に違反した場合のペナルティです。ペナルティが `Inf` に設定されている場合、それはハード制約として構築されます。
