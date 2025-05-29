```
 gtsylvi(A, B, C, D, E; mx, nx, abstol, reltol, maxiter) -> (X,info)
```

一般化T-Sylvester行列方程の解 `X` を計算します。

```
  ∑ A_i*X*B_i + ∑ C_j*transpose(X)*D_j = E,
```

ここで `A_i` と `C_j` は行次元が `E` の行次元と等しい行列であり、`B_i` と `D_j` は列次元が `E` の列次元と等しい行列です。 `A_i` と `B_i` はそれぞれ行列 `A` と `B` の `k`-ベクトルに含まれ、`C_j` と `D_j` はそれぞれ行列 `C` と `D` の `l`-ベクトルに含まれます。 コンポーネント行列のいずれかは `UniformScaling` として与えることができます。 キーワードパラメータ `mx` と `nx` は、データから推測できない場合に `X` の行と列の次元を指定するために使用できます。

最小二乗解 `X` は、適切に定義されたT-Sylvester線形演算子 `L:X -> Y` に適用される共役勾配ベースの反復法を使用して決定され、`L(X) = E` または `norm(L(X) - E)` が最小化されます。 キーワード引数 `abstol`（デフォルト: `abstol = 0`）と `reltol`（デフォルト: `reltol = sqrt(eps())`）は、計算された解の精度に対する望ましい許容誤差を提供するために使用でき、キーワード引数 `maxiter` は最大反復回数を設定するために使用できます（デフォルト: `maxiter = 1000`）。

*注:* 隣接方程式の導出については、参考文献 [1] を参照してください。これは、Juliaで一般的な線形行列方程式ソルバーを実装する動機ともなりました。

[1] Uhlig, F., Xu, A.B. Iterative optimal solutions of linear matrix equations for hyperspectral and multispectral image fusing. Calcolo 60, 26 (2023).      [https://doi.org/10.1007/s10092-023-00514-8](https://doi.org/10.1007/s10092-023-00514-8)
