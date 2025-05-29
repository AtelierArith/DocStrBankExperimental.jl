```
fload_Matrix_Sync(fileLocation,fileName)
```

`fileLocation`に保存された`fileName`に格納されたSおよびTマトリックスのみを読み込みます。

# 例

```julia-repl
    Matricies = fload_Matrix_Sync(fileLocation,fileName);
```

ファイルに保存されたデータのタプルを返します。フィールドは次のとおりです。

  * `SMatrix` : シンクロトロンの放射スペクトルの4Dマトリックス。
