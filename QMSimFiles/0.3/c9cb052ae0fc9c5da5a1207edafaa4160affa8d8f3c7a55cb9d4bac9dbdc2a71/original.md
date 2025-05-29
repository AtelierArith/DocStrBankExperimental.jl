```
map = read_maps(snpmapfile,qtlmapfile,qtleffectfile; ntr=0)
```

Read three map and effect files, and create a single map object, `QMSimMap`. With `ntr>0`, it returns the map object with QTL effects of `ntr` traits. In this case, the QTL effects will be loaded for trait 1; zero QTL effects will be assigned to the other traits.
