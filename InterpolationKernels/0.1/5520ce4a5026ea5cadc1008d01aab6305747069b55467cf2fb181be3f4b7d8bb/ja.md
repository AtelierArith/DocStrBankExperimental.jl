```
MitchellNetravaliSpline([T=Float64,] [b=1/3, c=1/3,] B=Flat)
```

は、浮動小数点型 `T`、パラメータ `b` と `c`、境界条件 `B` のための Mitchell & Netravali カーネルのインスタンスを生成します。

これらのカーネルは、2つのパラメータ `b` と `c` に依存する三次スプラインです。`(b,c)` の値に関わらず、これらのカーネルは正規化され、C¹ クラスの偶関数です（これらのカーネルとその1階導関数は連続です）。

`b = 0` を取ると、Keys のカーネルのファミリーが得られ、Mitchell & Netravali カーネルが基底関数であるための十分かつ必要な条件となります。

制約 `b + 2c = 1` を使用すると、少なくとも二次の近似を持つ三次フィルタが得られます。

`(b,c)` の特定の値は、他のよく知られたカーネルを生成します：

```
(b,c) = (1,0)       ==> 三次 B-スプライン
(b,c) = (0,-a)      ==> Keys の基底三次
(b,c) = (0,(1-a)/2) ==> 基底三次スプライン
(b,c) = (0,1/2)     ==> Catmull-Rom 三次
(b,c) = (b,0)       ==> Duff の張力 B-スプライン
(b,c) = (1/3,1/3)   ==> Mitchell-Netravali によって推奨
```

式 `ker'` は、Mitchell & Netravali カーネル `ker` の1階導関数であるカーネルインスタンスを生成します（コンストラクタ [`MitchellNetravaliSplinePrime`](@ref) も参照してください）。

参考文献：

  * Mitchell & Netravali, "*Reconstruction Filters in Computer Graphics*", in Computer Graphics, Vol. 22, Num. 4 (1988). http://www.cs.utexas.edu/users/fussell/courses/cs384g/lectures/mitchell/Mitchell.pdf.
