```
from_url(url::AbstractString; file_type::AbstractString = ".parquet")
```

URLからファイルを読み込み、キャッシュします。`file_type`は`".parquet"`、`".csv"`、または`".csv.gz"`のいずれかである必要があります。
