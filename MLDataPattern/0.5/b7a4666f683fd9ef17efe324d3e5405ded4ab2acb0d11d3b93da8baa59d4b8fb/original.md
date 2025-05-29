```
getobs(data, [idx], [obsdim])
```

Return the observation(s) in `data` that correspond to the given index/indices in `idx`. Note that `idx` can be of type `Int` or `AbstractVector`.

The returned observation(s) should be in the form intended to be passed as-is to some learning algorithm. There is no strict requirement that dictates what form or type that is. We do, however, expect it to be consistent for `idx` being an integer, as well as `idx` being an abstract vector, respectively.

If it makes sense for the type of `data`, `obsdim` can be used to specify which dimension of `data` denotes the observations. It can be specified in a type-stable manner as a positional argument (see `?LearnBase.ObsDim`), or more conveniently as a smart keyword argument.
