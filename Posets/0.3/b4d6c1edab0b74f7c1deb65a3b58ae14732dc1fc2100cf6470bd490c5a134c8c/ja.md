`Poset` は、要素 `{1,2,...,n}` の（厳密な）部分順序集合です。

基本コンストラクタ：

  * `Poset(n::Integer = 0)` は `n` 要素を持つポゼットを作成します（関係なし）。
  * `Poset(d::DiGraph)` は有向非巡回グラフのためのポゼットを作成します。
  * `Poset(p::Poset)` はコピーコンストラクタです。
