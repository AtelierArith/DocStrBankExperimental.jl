```
header_write(fid::IOStream, ht::NamedTuple)
```

`fid` にヘッダーを書き込みます

  * `fid::IOStream` は open(file, "w") から
  * `ht::NamedTuple` は `header_init()` または `header_read()` から
