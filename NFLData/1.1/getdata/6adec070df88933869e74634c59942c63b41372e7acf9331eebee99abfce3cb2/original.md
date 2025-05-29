```
from_url(url::AbstractString; file_type::AbstractString = ".parquet")
```

Reads a file from a URL and caches it. `file_type` can be one of `".parquet"`, `".csv"`, or `".csv.gz"`.
