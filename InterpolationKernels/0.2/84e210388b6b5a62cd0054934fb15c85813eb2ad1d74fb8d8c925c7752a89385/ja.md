```
MitchellNetravaliSpline{T}(b=1/3, c=1/3)
```

は、浮動小数点型 `T` とパラメータ `(b,c)` に対する Mitchell & Netravali カーネルのインスタンスを生成します。

これらのカーネルは、2つのパラメータ `b` と `c` に依存する三次スプラインです。 `(b,c)` の値に関わらず、Mitchell & Netravali カーネルは正規化され、偶数であり、C¹ 連続関数です（これらのカーネルとその一次導関数は連続です）。

`b = 0` を取ると、基準三次スプラインのファミリーが得られます（[`CardinalCubicSpline`](@ref) を参照）であり、Mitchell & Netravali カーネルが基準関数であるための十分かつ必要な条件です。

制約 `b + 2c = 1` を使用すると、少なくとも二次の近似を持つ三次フィルタが得られます。

特定の `(b,c)` の値は、他のよく知られたカーネルを生成します：

```
(b,c) = (1,0)      --> 三次 B-スプライン
(b,c) = (0,-a)     --> Keys の基準三次スプライン CardinalCubicSpline(a)
(b,c) = (0,1/2)    --> Catmull-Rom カーネル CatmullRomSpline()
(b,c) = (b,0)      --> Duff のテンション付き B-スプライン
(b,c) = (6β,-α-3β) --> 一般的な三次スプライン CubicSpline(α,β)
(b,c) = (1/3,1/3)  --> Mitchell-Netravali によって推奨される
```

式 `ker'` は、Mitchell & Netravali カーネル `ker` の1次導関数であるカーネルインスタンスを生成します（コンストラクタ [`MitchellNetravaliSplinePrime`](@ref) も参照してください）。

Mitchell & Netravali カーネルのファミリーは現在、[`CubicSpline`](@ref) のインスタンスです。

参考文献：

  * [Mitchell & Netravali, "*Reconstruction Filters in Computer Graphics*", in Computer Graphics, Vol. 22, Num. 4 (1988)](http://www.cs.utexas.edu/users/fussell/courses/cs384g/lectures/mitchell/Mitchell.pdf).
