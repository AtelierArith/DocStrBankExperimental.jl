function HGLET_jkl(GP::GraphPart, drow::Int, dcol::Int)

```
HGLET基底ベクトルに対応する(j,k,l)インデックスを生成します
    コエフィシエントdmatrix(drow,dcol)
```

### 入力引数

  * `GP`:    GraphPartオブジェクト
  * `drow`:  拡張コエフィシエントの行
  * `dcol`:  拡張コエフィシエントの列

### 出力引数

  * `j`: 拡張コエフィシエントのレベルインデックス
  * `k`: 拡張コエフィシエントのサブリージョンインデックス
  * `l`: 拡張コエフィシエントの固有ベクトルインデックス
