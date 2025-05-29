```
overlap(poly::PiecewiseLegendrePoly, f; 
    rtol=eps(T), return_error=false, maxevals=10^4, points=T[])
```

任意の関数 `f` と `poly` の重なり積分を評価します。

関数 `f` が与えられたとき、次の積分を評価します。

```
∫ dx f(x) poly(x)
```

適応ガウス・レジェンドル数値積分を使用して。

`points` は、積分区間内で被積分関数の局所的な困難が発生する可能性のあるブレークポイントのシーケンスです（例：特異点、不連続点）。
