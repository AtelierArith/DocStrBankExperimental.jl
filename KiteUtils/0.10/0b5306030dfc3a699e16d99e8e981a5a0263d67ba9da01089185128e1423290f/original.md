```
save_log(flight_log::SysLog, compress=true; path="")
```

Save a fligh log of type SysLog as .arrow file. By default lz4 compression is used,  if you use **false** as second parameter no compression is used.
