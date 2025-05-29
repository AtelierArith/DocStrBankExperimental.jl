```
AnnotationsSignal(records::Vector{Vector{TimestampedAnnotationList}})
```

Return `AnnotationsSignal(samples_per_record, records)` where `samples_per_record` is the minimum value required to write out each record completely (i.e. the maximum required `samples_per_record` across all records).
