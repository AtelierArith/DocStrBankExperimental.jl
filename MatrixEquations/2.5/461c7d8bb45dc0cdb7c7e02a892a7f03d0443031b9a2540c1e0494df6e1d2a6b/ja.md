```
hulyapci(U, Q; adj = false, abstol, reltol, maxiter) -> (X,info)
```

上三角行列 `U` とエルミート行列 `Q` に対して、連続 H-リャプノフ行列方程式の上三角解 `X` を計算します。

```
            U'*X + X'*U = Q   ただし adj = false の場合、
```

または

```
            U*X' + X*U' = Q    ただし adj = true の場合。
```

`n×n` の上三角行列 `U` に対して、最小二乗上三角解 `X` は、適切に定義された T-リャプノフ線形演算子 `L:X -> Y` に適用される共役勾配法に基づく反復法を使用して決定されます。この演算子は上三角行列 `X` を上三角行列 `Y` にマッピングし、関連する行列 `M = Matrix(L)` は $n(n+1)/2 \times n(n+1)/2$ です。キーワード引数 `abstol`（デフォルト: `abstol = 0`）と `reltol`（デフォルト: `reltol = sqrt(eps())`）は、計算された解の精度に対する望ましい許容誤差を提供するために使用できます。キーワード引数 `maxiter` は、最大反復回数を設定するために使用できます（デフォルト: `maxiter = 1000`）。  
