```
MRI(ref::MRI, nframes::Integer=ref.nframes)
```

Return an `MRI` structure whose header fields are populated based on a reference `MRI` structure `ref`, and whose image array are populated with zeros.

Optionally, the new `MRI` structure can be created with a different number of frames (`nframes`) than the reference MRI structure.
