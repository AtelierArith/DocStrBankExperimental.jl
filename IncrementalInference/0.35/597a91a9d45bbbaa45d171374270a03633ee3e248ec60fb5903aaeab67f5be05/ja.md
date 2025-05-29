```julia
drawTreeAsyncLoop(tree, opt; filepath, dotreedraw)

```

もしopt.drawtreeがtrueなら、opt.drawtreerateに従ってツリーを描画するための非同期タスクを開始します。

ノート

  * opt.drawtreeがfalseの場合は描画しません。呼び出し元に戻ります。
  * 現在は@asyncを使用しています。
  * `opt.showtree::Bool`を使用します。
  * solveTree!呼び出し中にopt.asyncを使用するとあまりうまく機能しませんが、ユーザーはこの関数を別々に使用できます。

開発ノート

  * TODO、Threads.@spawnを使用する。

関連

drawTree, drawGraph
