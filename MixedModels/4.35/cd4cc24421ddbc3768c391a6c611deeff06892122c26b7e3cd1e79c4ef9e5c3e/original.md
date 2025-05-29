```
response(m::MixedModel)
```

Return the response vector for the model.

For a linear mixed model this is a `view` of the last column of the `XyMat` field. For a generalized linear mixed model this is the `m.resp.y` field. In either case it should be copied if it is to be modified.
