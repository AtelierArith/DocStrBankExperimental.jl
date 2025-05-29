```julia
drawGraph(fgl; viewerapp, filepath, engine, show)

```

因子グラフ `<:AbstractDFG` をシステムの graphviz と xdot アプリを介して描画して表示します。

ノート

  * Linux に `sudo apt-get install xdot` のシステムインストールが必要です。
  * 外部プログラムを呼び出すべきではありません。
  * 長期的な解決策が必要です。
  * DFG の `toDotFile` がより良い解決策です – `xdot` アプリケーションで表示します。
  * `engine={"sfdp","fdp","dot","twopi","circo","neato"}` も試してください。

ノート：

  * 外部システムアプリケーション `xdot` を呼び出して `.dot` ファイル形式を読み取ります。

      * ```toDot(fg,file=...); @async run(`xdot file.dot`)```

関連

drawGraphCliq, [`drawTree`](@ref), printCliqSummary, spyCliqMat
