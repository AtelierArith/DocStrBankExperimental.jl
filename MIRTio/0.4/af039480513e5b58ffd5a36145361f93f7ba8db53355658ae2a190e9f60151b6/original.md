```
ht = header_string(ht::NamedTuple ; strip::Bool)
```

Convert each `Array{Cuchar}` to `String` in NamedTuple

in

  * `ht::NamedTuple` from `header_init()` or `header_read()`

option

  * `strip::Bool` strip tail white space characters from strings? default `false`

out

  * `ht::NamedTuple`
