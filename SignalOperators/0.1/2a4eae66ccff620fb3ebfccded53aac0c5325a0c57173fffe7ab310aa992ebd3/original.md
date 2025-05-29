```
filtersignal(x,h;[blocksize])
```

Apply the given filter `h` (from [`DSP`](https://github.com/JuliaDSP/DSP.jl)) to signal `x`. 

## Blocksize

Blocksize determines the size of the buffer used when computing intermediate values of the filter. It defaults to 4096. It need not normally be adjusted.
