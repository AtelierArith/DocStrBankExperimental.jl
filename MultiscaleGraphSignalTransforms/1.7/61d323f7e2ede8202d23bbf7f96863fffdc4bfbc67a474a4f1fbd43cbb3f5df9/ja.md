```
function NGWP_jkl(GP_star::GraphPart, drow::Int, dcol::Int)
```

NGWP基底ベクトルに対応する(j,k,l)インデックスを生成します。これは係数dmatrix(drow,dcol)に関連しています。

### 入力引数

  * `GP_star::GraphPart`: 双対グラフのGraphPartオブジェクト
  * `drow::Int`: 拡張係数の行
  * `dcol::Int`: 拡張係数の列

### 出力引数

  * `j`: 拡張係数のレベルインデックス
  * `k`: 拡張係数の双対グラフにおけるサブリージョンのインデックス
  * `l`: 拡張係数のタグ
