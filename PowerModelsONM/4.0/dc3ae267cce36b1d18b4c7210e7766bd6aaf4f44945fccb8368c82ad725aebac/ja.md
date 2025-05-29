```
parse_faults(
    faults_file::String;
    validate::Bool=true
)::Dict{String,Any}
```

故障 JSON 入力ファイルを解析します。これらは `PowerModelsProtection.build_mc_fault_stuides` の出力と同じ構造を持っています。

## 期待される JSON 構造

```json
{
    "bus_name": {
        "fault_type": {
            "fault_key": {
                "g": [ [200, -100, -100], [-100, 200, -100], [-100, -100, 200]],
                "b": [ [0, 0, 0], [0, 0, 0], [0, 0, 0]],
                "status": "ENABLED",
                "fault_type": "fault_type",
                "bus": "bus_name",
                "name": "fault_key",
                "connections": [1, 2, 3]
            }
        }
    }
}
```

ここで、`"fault_type"` は次のいずれかです：

  * `"3p"` : 3相
  * `"3pg"` : 3相-接地
  * `"ll"` : 相対相
  * `"llg"` : 相対相-接地
  * `"ll"` : 相対相

"bus_name" は任意で、ネットワークモデル内のバスの名前と一致する必要があります。

`"status"` は `PowerModelsDistribution.Status` Enum の文字列形式で、`"ENABLED"` または `"DISABLED"` のいずれかでなければなりません。

`"g"` と `"b"` は SI 単位の行列です。

最も深いレベルの `"fault_type"` は単なるメタデータであり、上記の `"fault_type"` キーと一致する必要があります。

`"name"` は故障キーと一致する必要があり、整数である必要があります。

`"connections"` は故障が適用される相を示す整数のベクターです。

詳細については、PowerModelsProtection の [documentation](https://github.io/lanl-ansi/PowerModelsProtection.jl) を参照してください。

## 検証

`validate=true`（デフォルト）である場合、解析されたデータ構造は最新の [Faults Schema](@ref Faults-Schema) に対して検証されます。
