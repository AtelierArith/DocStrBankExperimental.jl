```
google_download(url::AbstractString, location::Union{AbstractString,AbstractCmd,IO})
```

Download data from Google URL `url` into `location`, returning `location`.

`location` can be of any type that `Downloads.download` accepts - so a file path, a command, or an IO buffer.
