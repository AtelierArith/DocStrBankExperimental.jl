```
mv(src::AbstractPath, dst::AbstractPath; force=false)
```

Move the file or director from `src` to `dst`. An exist `dst` will only be overwritten if `force=true`.
