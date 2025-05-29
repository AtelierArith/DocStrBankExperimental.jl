```
AnnotationsSignal(records::Vector{Vector{TimestampedAnnotationList}})
```

`AnnotationsSignal(samples_per_record, records)`を返します。ここで`samples_per_record`は、各レコードを完全に書き出すために必要な最小値（すなわち、すべてのレコードにわたる最大の`samples_per_record`）です。
