```
t8_MPI_tag_t
```

t8code内部で使用される通信タグ。

| 列挙子                          | 注釈                          |
|:---------------------------- |:--------------------------- |
| T8*MPI*PARTITION_CMESH       | 粗いメッシュのパーティショニングに使用される      |
| T8*MPI*PARTITION_FOREST      | 森のパーティショニングに使用される           |
| T8*MPI*GHOST_FOREST          | ゴーストレイヤーの作成に使用される           |
| T8*MPI*GHOST*EXC*FOREST      | ゴーストデータの交換に使用される            |
| T8*MPI*TEST*ELEMENT*PACK_TAG | mpiのパックおよびアンパック機能のテストに使用される |
