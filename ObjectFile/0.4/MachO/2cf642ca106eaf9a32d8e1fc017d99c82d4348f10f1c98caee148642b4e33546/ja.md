```
MachOSegment
```

MachO `Segment` 型は、`MachOSegmentRef` からデリファレンスされたときに返されます。この型は型の整合性の目的でのみ存在します。実際の作業は `MachOSegmentCmd` 内で行われますが、すでに `MachOLoadCmd` から継承しているため、`Segment` からも継承することはできません。したがって、型階層を橋渡しするためにこのラッパー型が生まれました。
