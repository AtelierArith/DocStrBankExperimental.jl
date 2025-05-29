```
ERA5Dummy(;
    path  :: AbstractString = homedir(),
) -> ERA5Dummy <: ERA5Dataset
```

ERA5データセットのダミーを作成する関数で、ERA5 LandSeaマスクのパスに関する情報のみを含みます。

# キーワード引数

  * `path` : データを保存する指定されたディレクトリ
