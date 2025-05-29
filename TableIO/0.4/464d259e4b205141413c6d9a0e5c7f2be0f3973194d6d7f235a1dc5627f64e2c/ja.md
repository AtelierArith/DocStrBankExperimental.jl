```
write_table!(filename:: AbstractString, table; kwargs...):: AbstractString
```

`filename`: 出力ファイルのパスとファイル名 `table`: 保存用のTables.jl互換オブジェクト（例：DataFrame） `kwargs...`: 基本のファイル書き込み関数（例：`CSV.write`）に渡されるキーワード引数

例:

```
write_table!("my_output.csv", df)
```
