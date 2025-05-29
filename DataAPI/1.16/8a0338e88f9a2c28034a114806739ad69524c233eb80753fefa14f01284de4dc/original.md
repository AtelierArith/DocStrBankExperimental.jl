```
emptycolmetadata!(x, [col])
```

Delete all metadata for table `x` for column `col`. If `col` is not passed delete all column level metadata for table `x`. Throw an error if `x` does not support metadata deletion for column `col`.
