```
GrumpsThreads(; 
    blas = 0, 
    markets = 0, 
    inner = 0 
    )
```

This sets the number of threads to be used subject to a number of caveats.  *blas* refers to the number of BLAS threads, *markets* to the number of threads in loops over markets, and *inner* to the number of threads in inner loops.  A value of zero forces the automatic selection of the number of threads.

Of these, *inner* is not currently used at all, *market* is only used in *memsave* mode, and *blas* is used.  However, please note that the number of threads used by Grumps altogether is the number of threads passed in via the command line argument (i.e. via the -t switch), where that number does not include the number of BLAS threads set.
