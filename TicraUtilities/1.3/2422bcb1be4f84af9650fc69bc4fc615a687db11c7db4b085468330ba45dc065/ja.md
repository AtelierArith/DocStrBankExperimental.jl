```
write_torfile(fname::AbstractString, obj::TorObj; modestr = "w")
write_torfile(fname::AbstractString, objs::Vector{TorObj}; modestr = "w")
```

1つまたは複数の `TorObj` オブジェクトを Ticra 互換の TOR (Ticra Object Repository) ファイルに書き込みます。デフォルト値 `modestr = "w"` の場合、ファイルが存在しない場合は作成され、既に存在する場合は TOR オブジェクトを書き込む前に長さがゼロに切り詰められます。`modestr` の値を `"a"` に設定することで、既存のファイルにオブジェクトを追加することができます。
