```
emptyITensor([::Type{ElT} = NDTensors.EmptyNumber, ]inds)
emptyITensor([::Type{ElT} = NDTensors.EmptyNumber, ]inds::Index...)
```

Construct an ITensor with storage type `NDTensors.EmptyStorage`, indices `inds`, and element type `ElT`. If the element type is not specified, it defaults to `NDTensors.EmptyNumber`, which represents a number type that can take on any value (for example, the type of the first value it is set to).
