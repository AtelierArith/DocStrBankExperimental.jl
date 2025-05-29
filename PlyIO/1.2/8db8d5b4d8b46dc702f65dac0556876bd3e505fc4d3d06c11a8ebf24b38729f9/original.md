```
save_ply(ply::Ply, file; [ascii=false])
```

Save data from `Ply` data structure into `file` which may be a filename or an open stream.  The file will be native endian binary, unless the keyword argument `ascii` is set to `true`.
