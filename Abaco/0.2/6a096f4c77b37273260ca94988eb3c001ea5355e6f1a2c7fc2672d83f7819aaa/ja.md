```
ingest!(abaco, payload)
```

`payload` 辞書に含まれる入力変数を追加します。

Dict `msg` は `ts` と `ne` のキーと、入力変数として管理される他のキーを含む必要があります。

この関数は `payload` 辞書を修正します：`ne` と `ts` のキーがポップされます。

```julia
    payload = Dict(
        "ts" => nowts(),
        "ne" => "trento.castello",
        "x" => 23.2,
        "y" => 100
    )
    ingest!(abaco, ts, ne, payload)
```
