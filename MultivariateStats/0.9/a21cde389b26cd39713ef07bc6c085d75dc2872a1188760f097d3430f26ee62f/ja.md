```
fit(KernelPCA, X; ...)
```

行列 `X` に与えられたデータに対してカーネルPCAを実行します。`X` の各列は観測値です。

このメソッドは [`KernelPCA`](@ref) のインスタンスを返します。

**キーワード引数:**

`(d, n) = size(X)` をそれぞれ入力次元と観測数とします：

  * `kernel`: カーネル関数。この関数は2つのベクトル引数 `x` と `y` を受け取り、

スカラー値を返します（*デフォルト:* `(x,y)->x'y`）

  * `solver`: ソルバーの選択：

      * `:eig`: `LinearAlgebra.eigen` を使用します（*デフォルト*）
      * `:eigs`: `Arpack.eigs` を使用します（常にスパースデータに使用されます）
  * `maxoutdim`: 最大出力次元（*デフォルト* `min(d, n)`）
  * `inverse`: 非事前計算カーネルの逆変換の計算を行うかどうか（*デフォルト* `false`）
  * `β`: 逆変換を学習するリッジ回帰のハイパーパラメータ（`inverse` が `true` の場合の*デフォルト* `1`）。
  * `tol`: `eigs` ソルバーの収束許容値（*デフォルト* `0.0`）
  * `maxiter`: `eigs` ソルバーの最大反復回数（*デフォルト* `300`）
