```
CCIPCA(outdim::Int, indim; l::Int)
```

CCIPCA（Candid Covariance-free Incremental PCA）アルゴリズムを使用したオンラインPCAで、indimは受信ベクトルの長さ、outdimは投影する次元の数、lは忘却のレベルです。古いベクトルの重要性を徐々に低下させたい場合は、lの値を2-4の範囲に設定してください。つまり、最新のベクトルがより重視されます。

indimが指定されていない場合、最初のfit呼び出し時に後で設定されます。その後は固定され、変更できません。

CCIPCAは非常に高速でシンプルなオンラインPCAの近似です。高次元ベクトルを低次元（通常は2Dまたは3D）空間に投影するための次元削減に使用できます。このアルゴリズムは比較研究で非常に良い特性を示しており、高速でありながら（バッチ）PCAに対して良い近似を提供します。

# 例

```
o = CCIPCA(2, 10)                # 10次元ベクトルを2Dに投影
u1 = rand(10)
fit!(o, u1)                      # u1にフィット
u2 = rand(10)
fit!(o, u2)                      # u2にフィット
u3 = rand(10)
OnlineStats.transform(o, u3)     # u3をu1とu2にフィットしたPCA空間に投影するが、投影は変更しない
u4 = rand(10)
OnlineStats.fittransform!(o, u4) # u4にフィットし、その後u4を空間に投影
sort!(o)                         # 固有値の高い順にソート
o[1]                             # 主な（1番目の）固有ベクトルを取得
OnlineStats.relativevariances(o)         # 各固有ベクトルによって「説明される」変動を取得
```
