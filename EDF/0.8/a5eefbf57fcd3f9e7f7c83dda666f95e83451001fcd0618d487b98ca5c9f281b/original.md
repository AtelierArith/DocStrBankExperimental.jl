```
EDF.read!(file::File)
```

Read all EDF sample and annotation data from `file.io` into `file.signals` and `file.annotations`, returning `file`. If `eof(file.io)`, return `file` unmodified.
