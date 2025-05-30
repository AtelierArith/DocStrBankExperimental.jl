```
load_movielens_100k([path=nothing]) -> DataAccessor
```

`path` はローカルに保存された [MovieLens 100k](https://grouplens.org/datasets/movielens/100k/) を指します。フォルダー内のユーザー-アイテム-評価の三つ組を読み込み、それを `DataAccessor` インスタンスに変換します。

`path` が指定されていない場合や指定されたフォルダーが存在しない場合は、対応する zip ファイルをダウンロードして解凍します。
