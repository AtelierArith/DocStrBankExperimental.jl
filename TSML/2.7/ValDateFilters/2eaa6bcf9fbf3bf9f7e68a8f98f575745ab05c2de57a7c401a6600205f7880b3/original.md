```
transform!(dnnr::DateValMultiNNer,xx::T)
```

Replaces `missings` by nearest neighbor or linear interpolation by looping over the dataset  for each column until all missing values are gone.
