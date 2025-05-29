```
read_b2_output(filename::String)::Dict{String, Dict{String, Any}}
```

最終状態b2出力ファイル（b2fstateまたはb2time.nc）またはb2fgmtryファイルを読み込み、次の構造の辞書を返します: Dict("dim" => Dict{String, Any}, "data" => Dict{String, Any}) ここで "dim" はデータの次元を含み、"data" はデータ自体を含み、キーはフィールド名に対応します。

ファイル名を介してサポートされているSOLPSファイル:

  * b2fstate
  * b2fstati
  * b2time.nc
  * b2fgmtry
