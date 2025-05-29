```
collectPlm(x; m::Integer, lmax::Integer, [lmin::Integer = abs(m)], [kwargs...])
```

引数 `x` に対して関連するレジェンドル多項式 $P_\ell^m(x)$ を、次数 `l = lmin:lmax` と順序 `m` が `-l:l` にある場合に計算します。

インデックス `lmin:lmax` を持つ `v` を返し、`v[l] == Plm(x, l, m; kwargs...)` となります。

# オプションのキーワード引数

  * `norm`: 関数で使用される正規化。可能なオプションは `Val(:standard)`（デフォルト）、`Val(:normalized)`、`Val(:schmidtquasi)` または `Val(:schmidt)` です。

      * `norm = Val(:normalized)` の場合に得られる関数は L2 ノルムが $1$ です。
      * `norm = Val(:schmidtquasi)` の場合に得られる関数は L2 ノルムが $\sqrt{\frac{2(2-\delta_{m0})}{2l+1}}$ です。
      * `norm = Val(:schmidt)` の場合に得られる関数は L2 ノルムが $\sqrt{2(2-\delta_{m0})}$ です。
  * `csphase::Bool`: Condon-shortley 位相 $(-1)^m$ で、デフォルトで含まれています。
  * `Tnorm`: 正規化因子の型で、デフォルトでは動的に推測され、適切なコンテナの割り当てに使用されます。ノルムがオーバーフローなしに特定の型で表現できることがわかっている場合（例：`Float64`）、これを提供できます。`Tnorm` が引数として渡される場合は、オーバーフローを避けるように注意が必要です。

# 例

```jldoctest
julia> v = collectPlm(0.5, lmax = 3, m = 2);

julia> all(l -> v[l] ≈ Plm(0.5, l, 2), 2:3)
true

julia> v = collectPlm(0.5, lmax = 3, m = 2, norm = Val(:normalized));

julia> all(l -> v[l] ≈ Plm(0.5, l, 2, norm = Val(:normalized)), 2:3)
true
```
