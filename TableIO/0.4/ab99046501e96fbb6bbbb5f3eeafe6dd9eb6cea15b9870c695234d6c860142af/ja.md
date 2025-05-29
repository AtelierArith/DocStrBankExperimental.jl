```
read_table(filename:: AbstractString; kwargs...)
```

`filename`: 入力ファイルのパスとファイル名 `kwargs...`: 基本のファイル読み込み関数に渡されるキーワード引数 (例: `CSV.File`)

Tables.jl インターフェースに互換性のあるオブジェクトを返します。

例:

```
df = DataFrame(read_table("my_data.csv"; copycols=false))
```
