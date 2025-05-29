```
ingest(abaco, ts, ne, values)
```

入力変数を辞書 `values` に含めて追加します。

```julia
    # 現在のタイムスタンプ 
    ts = nowts()

    # ネットワークノードの短い名前
    ne = "trento.castello"

    values = Dict(
        "x" => 23.2,
        "y" => 100
    )
    ingest(abaco, ts, ne, values)
```
