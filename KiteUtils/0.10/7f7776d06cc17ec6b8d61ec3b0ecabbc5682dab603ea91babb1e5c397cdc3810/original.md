```
SysLog{P}
```

Flight log, containing the basic data as struct of vectors which can be accessed as if it would be an array structs.  In addition an extended view on the data that includes derived/ calculated values for plotting. Finally it contains meta data like the name of the log file.

  * `name::String`: name of the flight log
  * `colmeta::Dict`
  * `syslog::StructArrays.StructArray{KiteUtils.SysState{P}} where P`: struct of vectors that can also be accessed like a vector of structs
