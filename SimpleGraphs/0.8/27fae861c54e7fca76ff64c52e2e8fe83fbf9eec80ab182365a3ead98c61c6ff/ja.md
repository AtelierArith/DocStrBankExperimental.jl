`set_vertex_color(G::UndirectedGraph, d::Dict, palette)` は、`d` が頂点を整数にマッピングする辞書であり、`palette` が色のリストである関数です。

頂点を整数にマッピングを色に変換します。

頂点は次のように色が割り当てられます：頂点 `v` は色 `palette[k]` を取得し、ここで `k=d[v]` です。`palette` が省略された場合は、定数グローバル変数 `colorize_hues` を使用します。
