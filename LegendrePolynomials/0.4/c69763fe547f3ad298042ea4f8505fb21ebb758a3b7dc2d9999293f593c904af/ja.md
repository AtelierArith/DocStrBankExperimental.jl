```
collectPlm!(v::AbstractVector, x; m::Integer, [lmin::Integer = abs(m)], [lmax::Integer = length(v) - 1 + lmin], [kwargs...])
```

引数 `x` に対して関連するレジェンドル多項式 $P_\ell^m(x)$ を計算し、次数 `l = lmin:lmax` と順序 `m` が `-l:l` にあるものを `v` に格納します。

出力時に、`v[l + firstindex(v)] == Plm(x, l, m; kwargs...)` となるのは `l = lmin:lmax` の場合です。

# オプションのキーワード引数

  * `norm`: 関数で使用される正規化。可能なオプションは `Val(:standard)`（デフォルト）、`Val(:normalized)`、`Val(:schmidtquasi)` または `Val(:schmidt)` です。

      * `norm = Val(:normalized)` の場合に得られる関数は L2 ノルムが $1$ です。
      * `norm = Val(:schmidtquasi)` の場合に得られる関数は L2 ノルムが $\sqrt{\frac{2(2-\delta_{m0})}{2l+1}}$ です。
      * `norm = Val(:schmidt)` の場合に得られる関数は L2 ノルムが $\sqrt{2(2-\delta_{m0})}$ です。
  * `csphase::Bool`: Condon-shortley 位相 $(-1)^m$ で、デフォルトで含まれています。

# 例

```jldoctest
julia> v = zeros(2);

julia> collectPlm!(v, 0.5, lmax = 3, m = 2);

julia> all(zip(2:3, v)) do (l, vl); vl ≈ Plm(0.5, l, 2); end
true
```
