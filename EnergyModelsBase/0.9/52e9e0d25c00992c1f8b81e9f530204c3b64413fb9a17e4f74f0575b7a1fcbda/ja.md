```
CyclicPeriods{S<:NothingPeriod}
```

サイクリック制約を計算するための情報を含みます。パラメータ `S` は `AbstractStrategicPeriod` または `AbstractRepresentativePeriod` のいずれかである必要があります。

# フィールド

  * **`last_per::S`** は、`S<:AbstractRepresentativePeriod` の場合は最後の期間、`S<:AbstractStrategicPeriod` の場合は現在の期間であり、最後の戦略的期間は関連性がありません。
  * **`current_per::S`** は、`S<:AbstractRepresentativePeriod` と `S<:AbstractStrategicPeriod` の両方の場合における現在の期間です。
