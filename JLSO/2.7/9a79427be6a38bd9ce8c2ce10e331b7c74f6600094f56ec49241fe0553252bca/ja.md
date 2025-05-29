Juliaのシリアライズされたオブジェクト（JLSO）ファイル形式は、チェックポイントデータを保存するためのものです。

# 構造

.jlsoファイルは、特定のスキーマを持つ辞書を含むBSONファイルです。注意：生の辞書は、シリアライズされたオブジェクト自体が再構築できなくても、任意のBSONライブラリによって読み込むことができる必要があります。

例)

```
Dict(
    "metadata" => Dict(
        "version" => v"2.0",
        "julia" => v"1.0.4",
        "format" => :bson,  # :julia_serializeでも可
        "compression" => :gzip_fastest, # :none, :gzip_smallest, または :gzipでも可
        "image" => "xxxxxxxxxxxx.dkr.ecr.us-east-1.amazonaws.com/myrepository:latest"
        "project" => Dict{String, Any}(...),
        "manifest" => Dict{String, Any}(...),
    ),
    "objects" => Dict(
        "var1" => [0x35, 0x10, 0x01, 0x04, 0x44],
        "var2" => [...],
    ),
)
```

警告：シリアライズの`format`に関係なく、シリアライズされたオブジェクトは、異なるフィールドを持つ構造体にデシリアライズすることはできません。また、型がパッケージから名前変更されたり削除された場合も同様です。さらに、`:julia_serialize`形式は長期保存を目的としておらず、juliaのバージョン間でのポータビリティもありません。その結果、シリアライズされたオブジェクトデータをjsonファイルに保存しており、これによりdockerイメージとversioninfoを読み込んで再構築を可能にする必要があります。
