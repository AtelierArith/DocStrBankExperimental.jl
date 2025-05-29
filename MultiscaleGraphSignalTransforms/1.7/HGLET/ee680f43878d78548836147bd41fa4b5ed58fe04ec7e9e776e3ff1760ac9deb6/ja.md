function HGLET_Analysis(G::GraphSig, GP::GraphPart, gltype::Symbol = :L)

```
GraphSigオブジェクト'G'に対して、指定されたバージョンのグラフラプラシアン行列、すなわちL、Lrw、またはLsymに対応するHGLET展開係数の行列を生成します
```

### 入力引数

  * `G`:  GraphSigオブジェクト
  * `GP`: GraphPartオブジェクト
  * `gltype`: :L, :Lrw, または :Lsym、使用される固有ベクトルを示します

### 出力引数

  * `dmatrix`: 特定のGL行列を使用した展開係数の行列
