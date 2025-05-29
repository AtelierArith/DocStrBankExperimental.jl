```
multiseparate(img::Array, threshes, score; concavity=0.42, minarea = 10, dump = nothing)
```

Uses multiple thresholds to attempt to find the best separation of the distinct blobs in the image.  The best blob b is defined as the one that produces particles that produce smaller `score(b)`.  So a blob will be split if splitting the blob will produce multiple blobs of lower scores. The default function 'scorer(b::Blob)' looks for more circular blobs.
