`euler_char(G::UndirectedGraph)` は、関連する回転システムを持つグラフ `G` のオイラー特性を計算します。具体的には、`euler_char(G)` は `NV(G) - NE(G) + NF(G)` を返します。

*グラフが連結であり、少なくとも1つのエッジを持つことが必要です。*
