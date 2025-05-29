```
load_inventories() -> DataFrame
```

セクション7の[1]で詳述されている在庫ファイルを読み込み、ファイル形式情報に記載された変数に従って名前付けされた列を持つ`DataFrame`を返します。

```
------------------------------
変数       列       型
------------------------------
ID            1-11   文字
LATITUDE     13-20   実数
LONGITUDE    22-30   実数
ELEMENT      32-35   文字
FIRSTYEAR    37-40   整数
LASTYEAR     42-45   整数
------------------------------
```

[1] - https://www1.ncdc.noaa.gov/pub/data/ghcn/daily/readme.txt
