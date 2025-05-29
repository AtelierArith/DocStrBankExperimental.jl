```
readmeta(f::Function, file::AbstractString)
```

Do-block variant of `readmeta()`.  Use via something like:

```
readmeta("libfoo.so") do f
    ...
end
```
