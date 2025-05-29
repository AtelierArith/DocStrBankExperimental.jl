```
writemessage(handle::Message, filename::AbstractString; mode="wb")
```

Write the message respresented by `handle` to the file at `filename`.

`mode` is a mode as described by `Base.open`.
