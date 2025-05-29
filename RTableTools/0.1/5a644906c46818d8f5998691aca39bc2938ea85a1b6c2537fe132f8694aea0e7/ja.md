```
fread(file::AbstractString; header=true, kw...)
```

# 引数

  * `file`: 読み込むcsvファイル
  * `header`: csvファイルにヘッダーがあるか？
  * `kw`: `CSV.File`の他のパラメータ

# 例

```
fread("a.csv")
```
