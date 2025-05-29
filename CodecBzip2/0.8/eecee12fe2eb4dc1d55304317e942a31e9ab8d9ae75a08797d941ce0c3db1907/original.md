```
Bzip2Decompressor(;small=false, verbosity=0)
```

Create a bzip2 decompression codec.

## Arguments

  * `small`: flag to activate an algorithm which uses less memory
  * `verbosity`: verbosity level (0..4)

!!! warning
    `serialize` and `deepcopy` will not work with this codec due to stored raw pointers.

