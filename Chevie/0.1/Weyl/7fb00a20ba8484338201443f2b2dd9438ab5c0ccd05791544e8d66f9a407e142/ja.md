`relative_group(W::FiniteCoxeterGroup,J)`

`J` は `S==eachindex(gens(W))` の *distinguished* サブセットである必要があります。つまり、もし `s∈ S-J` の場合に $v(s,J)=w₀^{J∪ s}w₀ᴶ$ を設定すると、`J` はすべての `v(s,J)` によって安定しています。次に、$N_W(W_J)=W_J⋊ N₁$ であり、ここで `N₁` は `v(s,J)` によって生成される群で、これらは `N₁` のコクセター系を形成します。同等に、`N₁` は `N_W(W_J)` の `J`-縮約要素で構成されます。商 `R=N_W(W_J)/W_J` は $X(ZL_J/ZG)$ 上に自然な反射表現を持ち、[Lusztig1976](biblio.htm#Lus76) によれば、`W` の根の画像が $X(ZL_J)$ において根系を形成します。この関数は、いくつかの追加属性を持つ `R` を $X(ZL_J/ZG)$ 上の反射群として返します。

  * `R.relative_indices=setdiff(S,J)` は特定の順序で
  * `R.toparent=` は `.relative_indices` に対応する `v(s,J)` のリストです；`R→ N₁` の同型を定義します。
  * `R.fromparent` は `N₁` の要素を `R` にマッピングする関数です。`.toparent` への逆マッピングです。
