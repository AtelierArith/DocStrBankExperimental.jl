```
ht = header_read(fid::IOStream, hd::Matrix{Any} ; seek0::Bool)
```

Read header from scan file

in

  * `fid::IOStream` from open(file, "r")
  * `hd` header definition array (N × 3), e.g., from `header_example()`

option

  * `seek0::Bool` seek to `0` location in file first? default `true`

out

  * `ht::NamedTuple` with header values, accessed by ht.key
