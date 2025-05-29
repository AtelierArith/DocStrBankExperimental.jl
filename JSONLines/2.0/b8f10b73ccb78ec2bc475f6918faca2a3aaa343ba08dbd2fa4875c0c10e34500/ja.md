```
LineIterator(path::String; filestart = 1, structtype = nothing)
```

`path`にあるJSONLinesファイルのイテレータを作成します。

  * キーワード引数:

      * `filestart=1`: イテレータを開始する行
      * `structtype=nothing`: 各行に対して`JSON3.read`に渡されるStructType
