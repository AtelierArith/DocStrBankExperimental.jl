```
Plm(x, l::Integer, m::Integer; [kwargs...])
```

次数 `l` と順序 `m` の関連するレジェンドル多項式 $P_\ell^m(x)$ を計算します。`-l:l` の範囲にあります。

`m == 0` の場合、この関数はレジェンドル多項式を返します。

# オプションのキーワード引数

  * `norm`: 関数で使用される正規化。可能なオプションは `Val(:standard)`（デフォルト）、`Val(:normalized)`、`Val(:schmidtquasi)` または `Val(:schmidt)` です。

      * `norm = Val(:normalized)` で得られる関数は L2 ノルムが $1$ です。
      * `norm = Val(:schmidtquasi)` で得られる関数は L2 ノルムが $\sqrt{\frac{2(2-\delta_{m0})}{2l+1}}$ です。
      * `norm = Val(:schmidt)` で得られる関数は L2 ノルムが $\sqrt{2(2-\delta_{m0})}$ です。
  * `csphase::Bool`: Condon-shortley 位相 $(-1)^m$ で、デフォルトで含まれています。

# 例

```jldoctest
julia> Plm(0.5, 3, 2) ≈ 45/8 # 分析的に得られた値
true

julia> Plm(0.5, 4, 0) == Pl(0.5, 4)
true
```
