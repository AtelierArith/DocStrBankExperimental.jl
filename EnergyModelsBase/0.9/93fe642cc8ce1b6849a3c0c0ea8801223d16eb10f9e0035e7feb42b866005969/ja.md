```
struct CyclicRepresentative <: Cyclic
```

`StorageBehavior` は、運用時間を除く最も低い時間構造内で循環的な動作を実現します。

`TwoLevel{SimpleTimes}` の場合、このアプローチは `CyclicStrategic` に似ています。`TwoLevel{RepresentativePeriods{SimpleTimes}}` の場合、このアプローチは `CyclicStrategic` とは異なり、循環制約が各代表期間内で強制されます。
