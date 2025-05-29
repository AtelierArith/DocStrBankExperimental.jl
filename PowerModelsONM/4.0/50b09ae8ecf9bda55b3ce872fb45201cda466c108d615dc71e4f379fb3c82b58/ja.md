```
parse_network(
    network_file::String
)::Tuple{Dict{String,Any},Dict{String,Any}}
```

ランタイム引数で指定されたネットワークファイルを解析し、その基本ネットワーク、すなわちマルチネットワークに展開されていないものと、ネットワークのマルチネットワーク`ENGINEERING`表現を含むマルチネットワークを返します。
