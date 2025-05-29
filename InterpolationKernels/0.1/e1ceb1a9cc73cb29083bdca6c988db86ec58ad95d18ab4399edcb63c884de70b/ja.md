```
KeysSpline([T=Float64,] a, B=Flat)
```

は、浮動小数点型 `T`、パラメータ `a` および境界条件 `B` のための Keys ファミリーのカーディナルカーネルのインスタンスを生成します。

これらのカーネルは、1 でのスプラインの傾きである 1 つのパラメータ `a` に依存する区分的に正規化されたカーディナル三次スプラインです。Keys カーディナルカーネルは次のように定義されます：

```
ker(x) = p(abs(x))   if abs(x) ≤ 1
         q(abs(x))   if 1 ≤ abs(x) ≤ 2
         0           if abs(x) ≥ 2
```

ここで：

```
p(x) = 1 - (a + 3)*x^2 + (a + 2)*x^3
q(x) = -4a + 8a*x - 5a*x^2 + a*x^3
```

式 `ker'` は、Keys カーネル `ker` の 1 次導関数であるカーネルインスタンスを生成します（コンストラクタ [`KeysSplinePrime`](@ref) も参照してください）。

参考文献：

  * Keys, Robert, G., "Cubic Convolution Interpolation for Digital Image Processing", IEEE Trans. Acoustics, Speech, and Signal Processing, Vol. ASSP-29, No. 6, December 1981, pp. 1153-1160.
