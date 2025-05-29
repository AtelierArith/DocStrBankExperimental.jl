```
openblas_unpinthreads(; threadpool = :default)
```

Unpins all OpenBLAS threads by setting their affinity masks all unity. Afterwards, the OS is free to move any OpenBLAS thread from one CPU thread to another.
