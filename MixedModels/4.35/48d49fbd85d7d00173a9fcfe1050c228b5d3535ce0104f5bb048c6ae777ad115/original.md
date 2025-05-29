```
restoreoptsum!(m::MixedModel, io::IO; atol::Real=0, rtol::Real=atol>0 ? 0 : √eps)
restoreoptsum!(m::MixedModel, filename; atol::Real=0, rtol::Real=atol>0 ? 0 : √eps)
```

Read, check, and restore the `optsum` field from a JSON stream or filename.
