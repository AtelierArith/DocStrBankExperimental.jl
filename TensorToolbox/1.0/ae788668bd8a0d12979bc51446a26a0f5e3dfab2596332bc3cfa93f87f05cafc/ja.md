```
cp_als(X,R;init,tol,maxit,dimorder)
```

テンソル X の R コンポーネントによる CP 分解を計算します。

## 引数:

  * `init` ∈ {MatrixCell,"rand","nvecs","eigs"}。因子行列の初期推定値。init="nvecs"（"eigs" と同じ）である場合、行列は関数 nvecs で初期化されます。
  * `tol`: 許容誤差。デフォルト: 1e-4。
  * `maxit`: 最大反復回数。デフォルト: 1000。
  * `dimorder`: 次元の順序。デフォルト: 1:ndims(A)。
