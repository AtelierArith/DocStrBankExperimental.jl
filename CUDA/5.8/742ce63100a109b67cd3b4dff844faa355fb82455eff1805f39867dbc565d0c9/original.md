```
nextwarp(dev, threads)
prevwarp(dev, threads)
```

Returns the next or previous nearest number of threads that is a multiple of the warp size of a device `dev`. This is a common requirement when using intra-warp communication.
