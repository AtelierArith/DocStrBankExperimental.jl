```
Bzip2Compressor(;blocksize100k=9, workfactor=30, verbosity=0)
```

Create a bzip2 compression codec.

## Arguments

  * `blocksize100k`: block size to be use for compression (1..9)
  * `workfactor`: amount of effort the standard algorithm will expend before resorting to the fallback (0..250)
  * `verbosity`: verbosity level (0..4)

!!! warning
    `serialize` and `deepcopy` will not work with this codec due to stored raw pointers.

