```
read_b2time_output(filename::String)::Dict{String, Dict{String, Any}}
```

時間依存のb2出力ファイルを読み込み、次の構造の辞書を返します: Dict("dim" => Dict{String, Any}, "data" => Dict{String, Any}) ここで "dim" はデータの次元を含み、"data" はデータ自体を含み、キーはフィールド名に対応します。

ファイル名を介してサポートされているSOLPSファイル:

  * b2time.nc
