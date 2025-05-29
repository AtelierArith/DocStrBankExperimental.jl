```
pcaeigen(; kwargs...)
pcaeigen(X; kwargs...)
pcaeigen(X, weights::Weight; kwargs...)
pcaeigen!(X::Matrix, weights::Weight; kwargs...)
```

固有因子分解によるPCA。

  * `X` : Xデータ (n, p)。
  * `weights` : 観測値の重み (n)。    `Weight`型でなければなりません（例えば、関数`mweight`を参照）。

キーワード引数：

  * `nlv` : 主成分 (PC) の数。
  * `scal` : ブール値。`true`の場合、`X`の各列はその未修正標準偏差でスケーリングされます。

Dを重みの対角行列 (n, n) (`weights.w`) とし、XをDのメトリックで中心化された行列とします。この関数は、X' * D * Xの固有因子分解を計算することによって、メトリックDにおいて||X - T * V'||^2を最小化します。

例については関数`pcasvd`を参照してください。
