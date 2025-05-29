```
dlegendre(N, ϕ::T, n_max::Integer, m_max::Integer = -1; kwargs...) where T<:Number -> Matrix{float(T)}, Matrix{float(T)}
```

関連するレジェンドル関数 `P_n,m[cos(ϕ)]` の一階導関数を `ϕ` [rad] に関して計算します：

```
∂P_n,m[cos(ϕ)]
──────────────
     ∂ϕ
```

計算される最大次数は `n_max` で、最大次数は `m_max` です。`m_max` が `n_max` より大きい場合や負の場合（デフォルト）は、`n_max` に設定されます。

パラメータ `N` は正規化を選択します。以下の値が有効です：

  * `Val(:full)`: 完全に正規化された関連レジェンドル関数を計算します。
  * `Val(:schmidt)`: シュミット準正規化された関連レジェンドル関数を計算します。
  * `Val(:unnormalized)`: 非正規化された関連レジェンドル関数を計算します。

# キーワード

  * `ph_term::Bool`: `true` の場合、コンドン-ショートリー位相項 `(-1)^m` が含まれます。   (**デフォルト** = `false`)

# 戻り値

  * `Matrix{float(T)}`: レジェンドル関連関数 `P_n,m[cos(ϕ)]` の一階導関数を持つ行列。
  * `Matrix{float(T)}`: レジェンドル関連関数 `P_n,m[cos(ϕ)]` を持つ行列。

```
