```
D3Tree(node; detect_repeat=true, lazy_expand_after_depth=typemax(Int), kwargs...)
```

ブラウザやipythonノートブックで表示するためのツリーを構築します。`node`は、AbstractTreesインターフェースを実装する任意のオブジェクトです。

スタイルは、ノードのために`String`を返す以下の関数を実装することで制御できます：

```@docs
D3Trees.text(node)
D3Trees.tooltip(node)
D3Trees.style(node)
D3Trees.link_style(node)
```

`lazy_expand_after_depth`キーワード引数を通じて、大きなツリーの遅延読み込みを可能にします。この深さを超えるノードは、視覚化のために最初は展開されません。代わりに、それらはキャッシュされ、視覚化によって要求されたときにのみ展開されます。提供はD3Trees HTTPサーバーによって行われます。

サーバーは異なる視覚化のライフタイムに関する情報を持っていないため、過去の視覚化への参照を保持し続ける可能性があり、結果として多くのメモリを消費することがあります。サーバーをリセットして古いデータへの参照を削除するには、`D3Trees.reset_server()`または`D3Trees.shutdown_server()`を実行します。

# 引数

## 必須

  * `node`: `AbstractTrees.children(node)`および`AbstractTrees.printnode(io::IO, node)`を持つオブジェクト

## キーワード

  * `detect_repeat`: (デフォルト: true) trueの場合、ノードが以前に出現したかどうかを検出するために辞書を使用します
  * `lazy_expand_after_depth::Integer`: (デフォルト: typemax(Int)) `AbstractTrees.children(node)`がもはや呼び出されないツリーの深さを設定します。代わりに、この深さのノードはキャッシュされ、D3インタラクティブ視覚化でノードがクリックされたときにのみ`children(node)`が呼び出されます。ルートは深さ0を持つため、`lazy_expand_after_depth=1`を設定すると、ルートのみが展開されます。
  * `lazy_subtree_depth::Integer`: (デフォルト: 2) D3Treesサーバーから取得されるサブツリーの深さを設定します
  * `port::Integer`: (デフォルト: 16370) 視覚化のためにサブツリーを提供するD3Treesサーバーのポートを指定します。`shutdown_server(port)`でサーバーをシャットダウンします。
  * `dry_run_lazy_vizualization::Function`: (デフォルト: t -> D3Trees.dry*run*server(port, t)) 視覚化が開始される前に一度実行され、視覚化内での最初の取得を高速化する関数です。ツリーの子メソッドが最初の実行で長時間かかる場合は、カスタム関数を提供してください。
  * また、`D3Tree`コンストラクタのベクトルのベクトルの非ベクトル引数、すなわち`title`、`init_expand`、`init_duration`、`svg_height`もサポートしています。
