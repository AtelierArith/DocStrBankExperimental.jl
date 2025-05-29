```
log_histogram(logger, name, data::Vector; step=step(logger))
```

Bins the values found in `data` and logs them as an histogram under the tag `name`.
