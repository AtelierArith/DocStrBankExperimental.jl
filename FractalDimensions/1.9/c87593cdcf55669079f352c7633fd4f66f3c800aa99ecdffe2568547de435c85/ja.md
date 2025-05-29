```
correlationsum(X, ε::Real; w = 0, norm = Euclidean(), q = 2) → C_q(ε)
```

与えられた半径 `ε` と `norm` に対して、`X`（`StateSpaceSet` または時系列）の `q` 次相関和を計算します。キーワード `show_progress = true` を使用すると、大きな `X` の進行状況バーを表示できます。

```
correlationsum(X, εs::AbstractVector; w, norm, q) → C_q(ε)
```

`εs` がベクトルの場合、各 `ε ∈ εs` に対して `C_q` がより効率的に計算されます。利用可能なスレッド（`Threads.nthreads()`）に対してマルチスレッドも有効です。`X` の次元が小さく、`maximum(εs)` が `X` のサイズより小さい場合、関数 [`boxed_correlationsum`](@ref) の方が通常は速くなります。

## キーワード引数

  * `q = 2`: 相関和の次数
  * `norm = Euclidean()`: 距離ノルム
  * `w = 0`: タイラーウィンドウ
  * `show_progress = true`: 進行状況バーを表示

## 説明

相関和は `q=2` の場合、次のように定義されます：

$$
C_2(\epsilon) = \frac{2}{(N-w)(N-w-1)}\sum_{i=1}^{N}\sum_{j=1+w+i}^{N}
B(||X_i - X_j|| < \epsilon)
$$

`q≠2` の場合は次のようになります：

$$
C_q(\epsilon) = \left[ \sum_{i=1}^{N} \alpha_i
\left[\sum_{j:|i-j| > w} B(||X_i - X_j|| < \epsilon)\right]^{q-1}\right]^{1/(q-1)}
$$

ここで

$$
\alpha_i = 1 / (N (\max(N-w, i) - \min(w + 1, i))^{(q-1)})
$$

$$
N
$$

は `X` の長さであり、$B$ はその引数が `true` の場合に 1 を返します。`w` は [タイラーウィンドウ](@ref) です。

Grassberger の一般的な定義については、記事を参照してください [Grassberger2007](@cite) と、書籍 "Nonlinear Time Series Analysis" [Kantz2003](@cite) の第6章で `w` の最適値の選択に関する議論を、また第11.3章で q 次相関和の明示的な定義を確認してください。11.3の式は不正確ですが、ここで修正されており、インデックスは利用可能なすべての点を活用するように適応されています。また、$C_q$ を $1/(q-1)$ で即座に指数化することに注意してください。これにより、$C_q \propto \varepsilon ^\Delta_q$ として指数関数的にスケールします。
