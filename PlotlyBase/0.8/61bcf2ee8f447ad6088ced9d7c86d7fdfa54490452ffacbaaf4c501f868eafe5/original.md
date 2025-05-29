```
prependtraces!(p::Plot, update::AbstractDict, indices::AbstractVector{Int}=[1],
                maxpoints=-1)
```

The API for `prependtraces` is equivalent to that for `extendtraces` except that the data is added to the front of the traces attributes instead of the end. See Those docstrings for more information
