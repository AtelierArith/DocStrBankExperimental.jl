```
header(img::AstroImage)
```

Return the underlying FITSIO.FITSHeader object wrapped by an AstroImage. Note that this object has less flexible getindex and setindex methods. Indexing by symbol, Comment, History, etc are not supported.
