```
rebuild(g::SearchGraph; context=SearchGraphContext())
```

`SearchGraph`インデックスを再構築しますが、増分構築のために全データセットを参照します。つまり、元のアルゴリズムでは1..(i-1)の中のknnに接続するのに対し、1..nの可能な頂点の中でi番目の頂点をそのknnに接続できます。

# 引数

  * `g`: 再構築する検索インデックス。
  * `context`: 手続きを実行するためのコンテキストで、元のものとは異なる場合があります。
  * `minbatch`: マルチスレッドの方法を制御します。詳細は[`getminbatch`](@ref)を参照してください。
