```
CardinalCubicSpline{T}(a)
```

は、浮動小数点型 `T` とパラメータ `a = ker'(1)` のための Keys ファミリーのカーディナル三次スプラインのインスタンスを生成します。ここで、`ker(x)` の関数の傾きは `x = 1` でのものです。

これらのカーネルは、1つのパラメータ `a` に依存する C¹ 連続の区分的に正規化されたカーディナル三次スプラインであり、次のように定義されます：

```
ker(x) = 1 + ((2 + a)*|x| - (3 + a))*x^2    もし |x| ≤ 1
         a*(|x| - 1)*(|x| - 2)^2            もし 1 ≤ |x| ≤ 2
         0                                  もし |x| ≥ 2
```

式 `ker'` は、Keys カーネル `ker` の1次導関数であるカーネルインスタンスを生成します（コンストラクタ [`CardinalCubicSplinePrime`](@ref) も参照してください）。

参考文献：

  * Keys, Robert, G., "*Cubic Convolution Interpolation for Digital Image Processing*", IEEE Trans. Acoustics, Speech, and Signal Processing, Vol. ASSP-29, No. 6, December 1981, pp. 1153-1160.
