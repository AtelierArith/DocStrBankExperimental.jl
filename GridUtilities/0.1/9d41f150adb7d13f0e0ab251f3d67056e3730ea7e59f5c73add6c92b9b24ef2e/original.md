```
set_first_ghost!(h::History,h_pre::History)
```

Set the first ghost value of history `h` with the last element of history `h_pre`. This is only valid if `h` is of type `RegularHistory`.
