```
function parse_files(
    pm_file::String,
    pmd_file::String,
    pmitd_file::String;
    multinetwork::Bool=false
    auto_rename::Bool=false
)
```

PowerModels、PowerModelsDistribution、および PowerModelsITD 境界リンク入力ファイルを解析し、入力された辞書の結合情報を持つデータ辞書を返します。
