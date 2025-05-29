```
collectPl(x; lmax::Integer, [lmin::Integer = 0], [kwargs...])
```

引数 `x` と次数 `l = lmin:lmax` に対してレジェンドル多項式 $P_\ell(x)$ を計算します。インデックス `lmin:lmax` の `P` を返します。ここで `P[l] == Pl(x, l; kwargs...)` です。

# オプションのキーワード引数

  * `norm`: 関数で使用される正規化。可能なオプションは `Val(:standard)`（デフォルト）と `Val(:normalized)` です。`norm = Val(:normalized)` の場合に得られる関数は L2 ノルムが $1$ になります。

# 例

```jldoctest
julia> v = collectPl(0.5, lmax = 4);

julia> all(l -> v[l] ≈ Pl(0.5, l), 0:4)
true

julia> v = collectPl(0.5, lmax = 4, norm = Val(:normalized));

julia> all(l -> v[l] ≈ Pl(0.5, l, norm = Val(:normalized)), 0:4)
true
```
