```
read_city()
read_city(path::AbstractString)
```

Parse and return a [`City`](@ref), either from the default challenge data ([https://storage.googleapis.com/coding-competitions.appspot.com/HC/2014/paris_54000.txt](https://storage.googleapis.com/coding-competitions.appspot.com/HC/2014/paris_54000.txt)), or from a similarly formatted text file located at `path`.
