```
metadata(ctx::Context)
```

ファイルからScanImageメタデータセクションを読み取ります。

このデータセクションはTiff仕様の一部ではないため、一般的なTiffリーダーはこのデータにアクセスできません。

ScanImage 2016以降では、これはJSON文字列です。以前のバージョンのScanImageでは、これはMATLABでデシリアライズする必要があるバイト列です。

# 例

```jldoctest
ScanImageTiffReader.open(mytif) do io
    JSON.parse(metadata(io))
end
# 出力
Dict{String,Any} with 2 entries:
  "SI"        => Dict{String,Any}("hConfigurationSaver"=>Dict{String,Any}("usrF…
  "RoiGroups" => Dict{String,Any}("photostimRoiGroups"=>nothing,"imagingRoiGrou…
```
