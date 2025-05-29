```
edf_to_onda_annotations(edf::EDF.File, uuid::UUID)
```

Extract EDF+ annotations from an `EDF.File` for recording with ID `uuid` and return them as a vector of `Onda.Annotation`s.  Each returned annotation has a  `value` field that contains the string value of the corresponding EDF+ annotation.

If no EDF+ annotations are found in `edf`, then an empty `Vector{Annotation}` is returned.
