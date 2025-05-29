```
function parse_power_distribution_file(
    pmd_file::String,
    base_data::Dict{String,<:Any}=Dict{String, Any}();
    unique::Bool=true,
    multinetwork::Bool=false,
    auto_rename::Bool=false,
    ms_num::Int=1
)
```

`pmd_file`のファイル拡張子に応じて、電力分配ファイルを解析します。`base_data`は他のpmdシステムからのデータを含む辞書を表し（すべてのデータが結合される基盤として機能します）、`unique`は提供されたpmdデータが最初に渡されたものであるか、ユニークであるかを示します。`unique`でない場合、コンポーネントは追加される前に名前を変更する必要があります。名前が変更されたコンポーネント（該当する場合）を持つPowerModelsDistributionデータ構造のpmdネットワーク（辞書）を返します。
