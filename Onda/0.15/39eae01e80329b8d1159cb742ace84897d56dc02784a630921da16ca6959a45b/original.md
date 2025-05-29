```
@version MergedAnnotationV1 > AnnotationV1 begin
    from::Vector{UUID}
end
```

A Legolas-generated record type representing an annotation derived from "merging" one or more existing annotations.

This record type extends `AnnotationV1` with a single additional required field, `from::Vector{UUID}`, whose entries are the `id`s of the annotation's source annotation(s).

See https://github.com/beacon-biosignals/Legolas.jl for details regarding Legolas record types.
