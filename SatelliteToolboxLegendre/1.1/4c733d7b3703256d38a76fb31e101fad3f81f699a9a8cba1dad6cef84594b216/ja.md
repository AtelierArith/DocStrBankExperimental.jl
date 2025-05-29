```
legendre(N, ϕ::T, n_max::Integer, m_max::Integer = -1; ph_term::Bool = false) where T<:Number -> Matrix{float(T)}
```

関連するレジェンドル関数 `P_n,m[cos(ϕ)]` を計算します。計算される最大次数は `n_max` で、最大次数は `m_max` です。`m_max` が `n_max` より大きいか負（デフォルト）である場合、それは `n_max` に設定されます。

パラメータ `N` は正規化を選択します。以下の値が有効です：

  * `Val(:full)`: 完全に正規化された関連レジェンドル関数を計算します。
  * `Val(:schmidt)`: シュミット準正規化された関連レジェンドル関数を計算します。
  * `Val(:unnormalized)`: 非正規化された関連レジェンドル関数を計算します。

# キーワード

  * `ph_term::Bool`: `true` の場合、コンドン-ショートレー位相項 `(-1)^m` が含まれます。   (**デフォルト** = `false`)

# 戻り値

  * `Matrix{float(T)}`: レジェンドル関連関数 `P_n,m[cos(ϕ)]` を持つ行列。

# 備考

## 完全正規化

このアルゴリズムは **[1]** に基づいています。完全に正規化された関連レジェンドル関数の定義は **[2, p. 546]** で見ることができます。変換は次のように得られます：

```
         ┌                       ┐
         │  (n-m)! . k . (2n+1)  │
K_n,m = √│ ───────────────────── │,  k = (m = 0) ? 1 : 2.
         │         (n+m)!        │
         └                       ┘

P̄_n,m = P_n,m * K_n,m,
```

ここで `P̄_n,m` は完全に正規化されたレジェンドル関連関数です。

## シュミット準正規化

このアルゴリズムは **[3, 4]** に基づいています。変換は次のように得られます：

```
         ┌              ┐
         │      (n-m)!  │
K_n,m = √│ k . ──────── │,  k = (m = 0) ? 1 : 2.
         │      (n+m)!  │
         └              ┘

P̂_n,m = P_n,m * K_n,m,
```

ここで `P̂_n,m` はシュミット準正規化されたレジェンドル関連関数です。

# 参考文献

  * **[1]** Holmes, S. A. and W. E. Featherstone, 2002. A unified approach to the Clenshaw   summation and the recursive computation of very high degree and order normalised   associated Legendre functions. Journal of Geodesy, 76(5), pp. 279-299. 詳細情報:   http://mitgcm.org/~mlosch/geoidcookbook/node11.html
  * **[2]** Vallado, D. A (2013). Fundamentals of Astrodynamics and Applications. Microcosm   Press, Hawthorn, CA, USA.
  * **[3]** Schmidt, A (1917). Erdmagnetismus, Enzykl. Math. Wiss., 6, pp. 265–396.
  * **[4]** Winch, D. E., Ivers, D. J., Turner, J. P. R., Stening R. J (2005). Geomagnetism   and Schmidt quasi-normalization. Geophysical Journal International, 160(2), pp. 487-504.

```
