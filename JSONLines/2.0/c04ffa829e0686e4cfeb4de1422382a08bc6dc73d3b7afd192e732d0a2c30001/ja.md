```
LineIndex(path::String; filestart::Int = 0, skip::Int = 0, nrows::Int = typemax(Int), structtype = nothing, schemafrom::UnitRange{Int} = 1:10, nworkers::Int = 1)
```

`path`にあるJSONLinesファイルのインデックスを作成します。

  * キーワード引数:

      * `filestart=0`: ファイルを読み込む前にスキップするバイト数
      * `skip=0`: パースする前にスキップする行数
      * `nrows=typemax(Int)`: インデックスを作成する最大行数
      * `structtype=nothing`: 各行に対して`JSON3.read`に渡される`StructType`
      * `schemafrom=1:10`: 列名と列タイプを決定するために最初にパースする行
      * `nworkers=1`: `LineIndex`に対する操作に使用するスレッドの数
