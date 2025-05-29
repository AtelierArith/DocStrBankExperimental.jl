```
saveoptsum(io::IO, m::MixedModel)
saveoptsum(filename, m::MixedModel)
```

Save `m.optsum` (w/o the `lowerbd` field) in JSON format to an IO stream or a file

The reason for omitting the `lowerbd` field is because it often contains `-Inf` values that are not allowed in JSON.
