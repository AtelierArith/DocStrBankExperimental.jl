```
getindex_ref(collection, offset, stride, T, ref_type, idx)
```

Given a `collection`, such as `Sections`, `DynamicLinks`, etc... use the given `offset`, `stride`, and `T` parameters to read in and construct a `ref_type` object located at index `idx`.  Example invocation:

```
getindex_ref(
    sections,
    section_header_offset(oh),
    section_header_size(oh),
    section_header_type(oh),
    SectionRef,
    idx
)
```
