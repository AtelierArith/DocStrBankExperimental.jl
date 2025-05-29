```
function parse_power_transmission_file(
    pm_file::String;
    skip_correct::Bool = true,
    multinetwork::Bool=false,
    number_multinetworks::Int=0
)
```

`pm_file`から電力伝送ファイルを解析し、PowerModelsデータ構造のpmネットワーク辞書を返します。
