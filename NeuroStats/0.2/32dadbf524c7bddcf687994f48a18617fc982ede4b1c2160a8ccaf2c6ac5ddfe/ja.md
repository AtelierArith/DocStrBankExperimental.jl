```
make_table(; <keyword arguments>)
```

データをテーブルとして表示します。

# 引数

  * `header::Matrix{String}`: テーブルのヘッダー、例: `header = ["Group" "A" "B"]`
  * `data::Matrix{Any}`: テーブルのデータ、例: `data = ["var1" 1.0 2.0; "var2" 3.0 4.0]`

# 戻り値

何も返しません。
