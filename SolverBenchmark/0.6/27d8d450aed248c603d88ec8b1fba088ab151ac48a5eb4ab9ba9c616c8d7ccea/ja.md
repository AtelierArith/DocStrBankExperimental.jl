```
stats = load_stats(filename; kwargs...)
```

#### 引数

  * `filename::AbstractString`: 入力ファイル名。

#### キーワード引数

  * `key::String="stats"`: データが `filename` で読み込まれるキー。キーは `save_stats` が呼び出されたときに使用されたものと同じである必要があります。

#### 戻り値

ファイル `filename` に保存された統計を含む `Dict{Symbol,DataFrame}`。ユーザーは `load_stats` を呼び出す前に `import DataFrames` する必要があります。
