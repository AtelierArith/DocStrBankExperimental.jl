```
function GHWT_jkl(GP::GraphPart, drow::Int, dcol::Int; c2f::Bool = true)
```

GHWT基底ベクトルに対応する(j,k,l)インデックスを生成します。これは係数dmatrix(drow,dcol)に関連しています。

### 入力引数

  * `GP`: GraphPartオブジェクト
  * `drow`: 拡張係数の行
  * `dcol`: 拡張係数の列

### 出力引数

  * `j`: 拡張係数のレベルインデックス
  * `k`: 拡張係数のサブリージョンインデックス
  * `l`: 拡張係数のタグ
