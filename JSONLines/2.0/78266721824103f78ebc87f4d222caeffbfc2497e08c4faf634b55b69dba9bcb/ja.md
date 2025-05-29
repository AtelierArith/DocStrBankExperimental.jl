```
writelines(path::String, rows; nworkers = 1, mode = "w")
```

`rows`をJSONLinesファイル`path`に書き込みます

  * `path`: 出力ファイルへのパス
  * `rows`: `Tables.jl`互換のデータ
  * キーワード引数:

      * `nworkers=1`: JSONLinesへの解析に使用するスレッドの数
      * `mode="w"`: ファイルが開かれるモード。[I/Oとネットワークを参照](https://docs.julialang.org/en/v1/base/io-network/)
