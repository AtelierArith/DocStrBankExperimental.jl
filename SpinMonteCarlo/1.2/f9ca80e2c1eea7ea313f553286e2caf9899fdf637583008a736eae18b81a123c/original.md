```
load_snapshot(io, splitter)
load_snapshot(filename, splitter)
```

load snapshot from `io` or `filename`. `splitter` is the set of field splitter and will be passed `Base.split` as the second argument (see the doc of `Base.split`).
