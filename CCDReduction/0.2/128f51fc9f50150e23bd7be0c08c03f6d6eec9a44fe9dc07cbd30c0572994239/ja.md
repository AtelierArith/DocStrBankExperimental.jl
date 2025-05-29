```
filenames(collection)
```

データフレーム内のエントリのファイル名のジェネレーター。

`collection`を各`path`を使用して反復処理します。

# 例

```julia
collection = fitscollection("~/data/tekdata")
for path in filenames(collection)
    @assert path isa String
    println(path)
end

# 出力
"~/data/tekdata/tek001.fits"
"~/data/tekdata/tek002.fits"
...
```
