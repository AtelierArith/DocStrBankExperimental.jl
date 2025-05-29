```
deletecolmetadata!(x, col, key::AbstractString)
```

Delete metadata for table `x` for column `col` for key `key` and return `x` (if metadata for `key` is not present do not perform any action). Throw an error if `x` does not support metadata deletion for column `col`.
