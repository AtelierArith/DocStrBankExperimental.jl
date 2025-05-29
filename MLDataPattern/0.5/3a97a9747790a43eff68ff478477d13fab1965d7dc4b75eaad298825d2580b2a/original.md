```
getobs!(buffer, data, [idx], [obsdim]) -> buffer
```

Write the observation(s) from `data` that correspond to the given index/indices in `idx` into `buffer`. Note that `idx` can be of type `Int` or `AbstractVector`.

Unless explicitly implemented for `data` it defaults to returning `getobs(data, idx, obsdim)` in which case `buffer` is ignored.

If it makes sense for the type of `data`, `obsdim` can be used to specify which dimension of `data` denotes the observations. It can be specified in a type-stable manner as a positional argument (see `?LearnBase.ObsDim`), or more conveniently as a smart keyword argument.
