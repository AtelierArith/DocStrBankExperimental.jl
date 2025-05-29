```
read_files(path; args)
```

汎用ファイルリーダーで、タイプを自動的に検出し、適切な読み取り関数を呼び出します。

# 引数

  * `path` : 読み取るファイルのパスを含む文字列
  * `args` : 特定のファイルタイプに対してサポートされる追加の引数は、通常通りに指定されます

# 例

```jldoctest
julia> df = DataFrame(ID = 1:5, Name = ["Alice", "Bob", "Charlie", "David", "Eva"], Score = [88, 92, 77, 85, 95]);

julia> write_parquet(df, "test.parquet");

julia> read_file("test.parquet")
5×3 DataFrame
 Row │ ID     Name     Score 
     │ Int64  String   Int64 
─────┼───────────────────────
   1 │     1  Alice       88
   2 │     2  Bob         92
   3 │     3  Charlie     77
   4 │     4  David       85
   5 │     5  Eva         95
```
