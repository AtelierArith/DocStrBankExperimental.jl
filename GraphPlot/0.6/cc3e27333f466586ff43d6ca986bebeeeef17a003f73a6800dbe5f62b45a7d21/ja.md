グラフレイアウトをストレスメジャライゼーションを使用して計算する

入力:

```
δ: ペアワイズ距離の行列
p: 埋め込みの次元 (デフォルト: 2)
w: 重みの行列。指定されていない場合、デフォルトは
       w[i,j] = δ[i,j]^-2 (δ[i,j]が非ゼロの場合) またはそれ以外は0
X0: レイアウトの初期推定。座標は行で与えられます。
    指定されていない場合、デフォルトはガウス分布のランダム行列
```

追加のオプションキーワード引数は、アルゴリズムの収束と要求された追加出力を制御します:

```
maxiter:   最大反復回数。デフォルト: 400size(X0, 1)^2
abstols:   ストレスの収束のための絶対許容誤差。
           反復は、2つの連続するストレスの差がabstol未満になると終了します。
           デフォルト: √(eps(eltype(X0))
reltols:   ストレスの収束のための相対許容誤差。
           反復は、現在のストレスに対する2つの連続するストレスの差が
           reltol未満になると終了します。デフォルト: √(eps(eltype(X0))
abstolx:   レイアウトの収束のための絶対許容誤差。
           反復は、2つの連続するレイアウトのフロベニウスノルムが
           abstolx未満になると終了します。デフォルト: √(eps(eltype(X0))
verbose:   trueの場合、各反復で収束情報を印刷します。
           デフォルト: false
returnall: trueの場合、すべての反復とそれに関連するストレスを返します。
           false (デフォルト) の場合、最後の反復を返します
```

出力:

```
最終レイアウトX。座標は行で与えられます。returnall=trueの場合を除く。
```

参考文献:

```
解くべき主な方程式は次の通りです (8):

@incollection{
    author = {Emden R Gansner and Yehuda Koren and Stephen North},
    title = {Graph Drawing by Stress Majorization}
    year={2005},
    isbn={978-3-540-24528-5},
    booktitle={Graph Drawing},
    seriesvolume={3383},
    series={Lecture Notes in Computer Science},
    editor={Pach, J'anos},
    doi={10.1007/978-3-540-31843-9_25},
    publisher={Springer Berlin Heidelberg},
    pages={239--250},
}
```
