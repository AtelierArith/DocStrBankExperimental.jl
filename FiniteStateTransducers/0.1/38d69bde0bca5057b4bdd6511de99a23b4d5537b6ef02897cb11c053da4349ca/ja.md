`shortest_distance(fst[, s=get_initial(fst); filter=arc->true, reverse=false)`

状態 `s` から他のすべての状態への最短距離を計算します。状態 `s` と `i` の間の最短距離は、これらの状態間のすべてのパスの重みの合計として定義されます。

重みは右分配的であり、k-閉じている必要があります。

`fst` に `N` 状態がある場合、`N` 長のベクトルが返され、`i` 番目の要素には状態 `s` と `i` の間の最短距離が含まれます。

`reversed==true` の場合、最終状態からの最短距離が計算されます。この場合、`s` は影響を与えず、逆WFSTに新しい初期スーパー状態が追加されます。ここでは、重みは左分配的であり、k-閉じている必要があります。

Mohri "Semiring framework and algorithms for shortest-distance problems", Journal of Automata, Languages and Combinatorics 7(3): 321-350, 2002 を参照してください。
