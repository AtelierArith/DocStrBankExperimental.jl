```
transform(nc::Knc, kernel::Function, X, normalize!::Function=softmax!)
```

Maps a collection of objects to the vector space defined by each center in `nc`; the `kernel` function is used measure the similarity between each $u \in X$ and each center in nc. The normalization function is applied to each vector (normalization methods needing to know the attribute's distribution can be applied on the output of `transform`)
