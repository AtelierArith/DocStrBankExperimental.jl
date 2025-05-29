## SCOMPONENTS

```
グラフの強連結成分を計算する

ci=scomponents(A) は、グラフ A のすべての頂点の成分番号のインデックスを返します。成分の総数は最大値 ci です。
入力が無向の場合、このアルゴリズムは接続成分のみを出力します。それ以外の場合、強連結成分を出力します。

この実装は、タージャンの1972年の論文「深さ優先探索と線形グラフアルゴリズム」に基づいています。SIAMのComputingジャーナル、1972年、1巻、pp.146-160。
```

## 関数

  * `cc = scomponents(A::MatrixNetwork)`
  * `cc = scomponents{T}(A::SparseMatrixCSC{T,Int64})`
  * `sci = strong_components_map(A::MatrixNetwork)`
  * `sci = strong_components_map{T}(A::SparseMatrixCSC{T,Int64})`
  * `sc_rich = enrich(cc::Strong_components_output) # check ?enrich for more`

## 例

```
A = load_matrix_network("cores_example")
cc = scomponents(A)
scomponents(A).number
scomponents(A).sizes      
scomponents(A).map  
strong_components_map(A)     # マップだけが必要な場合
enrich(scomponents(A)) # 追加の強化された出力を生成

# [ei,ej] で動作可能
ei = [1;2;3]
ej = [2;4;1]
cc = scomponents(ei,ej)

# スパース行列 A で動作可能
A = sprand(5,5,0.5)
cc = scomponents(A)
```
