```
read_rdata(path)
```

Read `.rdata` and `.rds` files as DataFrame. `.rdata` files will result in a `Dict`. Dataframes can then be selected with `result["name"]`

# Arguments

  * `path`: A string with the file location. This does not yet support reading from URLs.
