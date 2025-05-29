```
Dict(rec::Record)
```

Extracts the `Record` and its properties into a `Dict`

!!! warn
    On `AttributeRecord`s this may be an expensive operation, so you probably don't want to do this for every log record unless you're planning on using every `Attribute`.

