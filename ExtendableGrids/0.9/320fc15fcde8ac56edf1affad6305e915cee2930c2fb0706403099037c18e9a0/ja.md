```julia
function glue(g1,g2;             g1regions=1:num*bfaceregions(g1),             g2regions=1:num*bfaceregions(g2),             interface=0,             tol=1.0e-10)

二つのグリッドを共通の境界ファセットに沿ってマージします。

  * g1: マージされる最初のグリッド
  * g2: マージされる二番目のグリッド
  * g1regions: グリッド1から使用される境界領域。デフォルト: すべて。
  * g2regions: グリッド2から使用される境界領域。デフォルト: すべて。
  * interface: ゼロでない場合、新しいグリッドにインターフェース領域を作成します。そうでない場合は無視します。
  * tol: 二つの点が同一と見なされる距離。デフォルト: 1.0e-10

非推奨:

  * breg: インターフェースの古い表記
```
