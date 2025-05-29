```
quality(v::Variation, r::Union{SAM.Record,BAM.Record}) -> Float64
```

Get the phred-scalled basecall quality of `v` within the sequencing read of `r`.
