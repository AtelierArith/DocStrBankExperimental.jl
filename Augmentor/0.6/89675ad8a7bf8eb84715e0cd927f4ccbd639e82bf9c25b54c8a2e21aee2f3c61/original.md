```
testpattern([T=RGBA{N0f8}]; ratio=1.0) -> Matrix{RGBA{N0f8}}
```

Load and return the provided 300x400 test image. Additional args and kwargs are passed to `imresize`.

The returned image was specifically designed to be informative about the effects of the applied augmentation operations. It is thus well suited to prototype an augmentation pipeline, because it makes it easy to see what kind of effects one can achieve with it.
