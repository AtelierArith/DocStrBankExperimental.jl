```
convertlabel(new_encoding, vec::AbstractVector, [old_encoding]) -> (Readonly)MappedArray
```

Creates a lazy view into `vec` that makes it look like it is in the encoding specified by `new_encoding`, while it is actually preserved as being of `old_encoding`.

This method only works for label-encodings that are vector-based (i.e. pretty much all but `OneOfK`). The resulting MappedArray will be writeable unless `old_encoding` is of type `OneVsRest`, in which case the result will be a `ReadonlyMappedArray`.
