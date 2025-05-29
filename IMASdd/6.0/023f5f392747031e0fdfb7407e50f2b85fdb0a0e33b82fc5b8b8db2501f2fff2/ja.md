```
json2imas(filename::AbstractString, @nospecialize(ids::IDS)=dd(); error_on_missing_coordinates::Bool=true, show_warnings::Bool=true)
```

指定された `filename` の JSON ファイルから IMAS データ構造をロードします。
