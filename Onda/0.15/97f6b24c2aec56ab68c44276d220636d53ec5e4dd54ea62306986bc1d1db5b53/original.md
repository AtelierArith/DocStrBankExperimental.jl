```
merge_overlapping_annotations([predicate=TimeSpans.overlaps,] annotations)
```

Given the `onda.annotation@1`-compliant table `annotations`, return a `Vector{MergedAnnotationV1}` where "overlapping" consecutive entries of `annotations` have been merged using `TimeSpans.shortest_timespan_containing`.

Two consecutive annotations `a` and `b` are determined to be "overlapping" if `a.recording == b.recording && predicate(a.span, b.span)`. Merged annotations' `span` fields are generated via calling `TimeSpans.shortest_timespan_containing` on the overlapping set of source annotations.

Note that every annotation in the returned table has a freshly generated `id` field and a non-empty `from` field. An output annotation whose `from` field only a contains a single element corresponds to an individual non-overlapping annotation in the provided `annotations`.

Note that this function internally works with `Tables.columns(annotations)` rather than `annotations` directly, so it may be slower and/or require more memory if `!Tables.columnaccess(annotations)`.

See also `TimeSpans.merge_spans` for similar functionality on generic time spans (instead of annotations).
