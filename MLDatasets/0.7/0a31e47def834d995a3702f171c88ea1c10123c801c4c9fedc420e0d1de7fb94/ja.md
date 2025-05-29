```
OrganicMaterialsDB(; split=:train, dir=nothing)
```

バルク有機結晶の有機材料データベース（OMDB）からのOMDB-GAP1 v1.1データセット。

データセットは手動で https://omdb.mathub.io/dataset からダウンロードし、解凍して、そのファイル内容を `OrganicMaterialsDB` フォルダーに配置する必要があります。

データセットには以下のファイルが含まれています：

|          ファイル名 |                                                           説明 |
| --------------:| ------------------------------------------------------------:|
| structures.xyz |    12500の結晶構造。最初の10000をトレーニング例として使用し、残りの2500をテストセットとして使用します。 |
|   bandgaps.csv |                          structures.xyzに対応する12500のDFTバンドギャップ |
|     CODids.csv | 12500のCOD IDが結晶構造データベース（structures.xyzと同じ順序）をクロスリファレンスしています。 |

このデータセットを紹介する論文を引用してください： https://arxiv.org/abs/1810.12814
