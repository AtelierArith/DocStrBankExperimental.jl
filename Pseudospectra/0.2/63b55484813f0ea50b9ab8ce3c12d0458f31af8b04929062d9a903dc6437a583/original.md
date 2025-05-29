```
zoomin!(ps_data,z,ax) -> Int
```

update `ps_data` to include a finer resolution portrait.

Returns -1 for invalidity, 0 for return to an existing zoom (requiring a redraw), and 1 for establishment of new one (requiring a recalculation and redraw).
