```
fold(io, hdrs)
```

Compute the fold of a frame where io is JSeis corresponding to the dataset, and hdrs are the headers for the frame. For example: `io=jsopen("file.js"); fold(io, readframehdrs(io,1))`
