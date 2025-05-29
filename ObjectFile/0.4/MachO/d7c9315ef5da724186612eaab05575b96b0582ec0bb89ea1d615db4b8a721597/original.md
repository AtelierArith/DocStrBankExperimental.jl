```
MachOSegmentRef
```

MachO `SegmentRef` type which is returned from a `MachOSegments` when it is indexed into.  Note that this type exists only for the purposes of type conformity; all the real work is done within `MachOSegmentCmd`; but since that already inherits from `MachOLoadCmd`, and we needed a `MachOSegment` type that would inherit from `Segment`, we figured might as well make a `MachOSegmentRef` as well to keep things nice and symmetric.
