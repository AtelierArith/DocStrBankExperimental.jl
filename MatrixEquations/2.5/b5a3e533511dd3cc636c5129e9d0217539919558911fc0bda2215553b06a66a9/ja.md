```
tlyapci(A, C, isig = +1; adj = false, abstol, reltol, maxiter) -> (X,info)
```

連続T-リャプノフ行列方程式の解 `X` を計算します。

```
            A*X +isig*transpose(X)*transpose(A) = C   ただし adj = false の場合、
```

または

```
            A*transpose(X) + isig*X*transpose(A) = C   ただし adj = true の場合、
```

ここで `isig = 1` の場合、`C` は対称行列であり、`isig = -1` の場合、`C` は反対称行列です。

行列 `A` に対して、最小二乗解 `X` は、適切に定義されたT-リャプノフ線形演算子 `L:X -> Y` に適用される共役勾配法に基づいて決定されます。ここで `L(X) = C` または `norm(L(X) - C)` が最小化されます。キーワード引数 `abstol`（デフォルト: `abstol = 0`）と `reltol`（デフォルト: `reltol = sqrt(eps())`）は、計算された解の精度に対する望ましい許容誤差を提供するために使用でき、キーワード引数 `maxiter` は最大反復回数を設定するために使用できます（デフォルト: `maxiter = 1000`）。
