```
issame(file1, file2, tol=1e-4; strict=true, verbose=false) -> Bool
```

Check if two VLSV files `file1` and `file2` are approximately identical, under relative tolerance `tol`. If `strict=true`, the file size difference should be less than 1%.
