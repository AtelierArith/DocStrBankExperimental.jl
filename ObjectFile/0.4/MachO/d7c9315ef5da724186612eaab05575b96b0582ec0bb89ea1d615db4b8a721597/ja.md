```
MachOSegmentRef
```

MachO `SegmentRef` 型は、`MachOSegments` からインデックスされたときに返されます。この型は型の整合性の目的でのみ存在します。実際の作業は `MachOSegmentCmd` 内で行われますが、すでに `MachOLoadCmd` から継承されているため、`Segment` から継承する `MachOSegment` 型が必要でした。そのため、物事をきれいで対称的に保つために `MachOSegmentRef` も作成することにしました。
