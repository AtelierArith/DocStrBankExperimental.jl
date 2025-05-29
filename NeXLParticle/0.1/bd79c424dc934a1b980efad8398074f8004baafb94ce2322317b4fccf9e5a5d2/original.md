```
blob(img::AbstractArray, thresh::Function)::Vector{Blob}
```

Create a Vector of `Blob`s containing discontiguous regions meeting the threshold function.  The result is sorted by `Blob` area.
