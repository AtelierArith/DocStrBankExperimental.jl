```
fload_Matrix_SyncISO(fileLocation,fileName)
```

`fileLocation`に保存された`fileName`に格納されたSおよびTマトリックスを読み込み、角度を合計することによって各等方的形式に変換します。（マトリックスの次元は同じままで、すなわち6D->6Dで、3つの次元のサイズは1です）

# 例

```julia-repl
    Matricies = fload_Matrix_SyncISO(fileLocation,fileName);
```

ファイルに保存されたデータのタプルを返します。フィールドは次のとおりです：

  * `SMatrix` : シンクロトロンの放射スペクトルの4Dマトリックス。
