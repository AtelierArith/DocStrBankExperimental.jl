```
isrelativeurl(str)
```

与えられた文字列が相対URLであるかどうかをチェックします。

julia> isrelativeurl("../path/to/directory") true julia> isrelativeurl("./**file**") true julia> isrelativeurl("foo:bar") false
