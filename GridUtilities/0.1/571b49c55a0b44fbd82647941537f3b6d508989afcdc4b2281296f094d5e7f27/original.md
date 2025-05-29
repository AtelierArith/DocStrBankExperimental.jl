```
save(t,R::WritePlan,v)
```

Check if time `t` is appropriate for writing to file, according to the WritePlan `R`, and if so, write the specified variables `v` (which may be separated by commas) in `R` to the file in `R`.
