```
X = sylvci(A,B,C)
```

連続シルベスター行列方程式を解きます。

```
            AX + XB = C ,
```

ここで `A` と `B` は正方行列です。

最小二乗解 `X` は、適切に定義されたリャプノフ線形演算子 `L:X -> Y` に適用される共役勾配法に基づく反復法を使用して決定されます。ここで `L(X) = C` または `norm(L(X) - C)` が最小化されます。キーワード引数 `abstol`（デフォルト: `abstol = 0`）と `reltol`（デフォルト: `reltol = sqrt(eps())`）を使用して、計算された解の精度に対する望ましい許容誤差を提供できます。また、キーワード引数 `maxiter` を使用して最大反復回数を設定できます（デフォルト: `maxiter = 1000`）。
