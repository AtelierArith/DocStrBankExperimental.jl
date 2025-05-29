```
MachOSegment
```

MachO `Segment` type which is returned from a `MachOSegmentRef` when it is dereferenced.  Note that this type exists only for the purposes of type conformity; all the real work is done within `MachOSegmentCmd`; but since that already inherits from `MachOLoadCmd`, it cannot also inherit from `Segment`. Thus, this wrapper type was born to bridge the type hierarchy.
