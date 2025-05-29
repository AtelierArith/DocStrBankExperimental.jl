```
process_file(filename[, folder]) -> FileCoverage
```

Given a .jl file and its containing folder, produce a corresponding `FileCoverage` instance from the source and matching coverage files. If the folder is not given it is extracted from the filename.
