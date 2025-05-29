```
load_scanning_strategy(io::IO) -> ScanningStrategy
load_scanning_strategy(filename::AbstractString) -> ScanningStrategy
```

JSONファイル`io`に見つかった定義から`ScanningStrategy`オブジェクトを作成するか、パス`filename`のJSONファイルから作成します。詳細は[`load_scanning_strategy`](@ref)を参照してください。
