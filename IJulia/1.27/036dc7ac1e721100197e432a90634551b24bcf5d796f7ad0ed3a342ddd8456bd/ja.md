**IJulia** は、[Julia言語](http://julialang.org/) バックエンドと [Jupyter](http://jupyter.org/) インタラクティブ環境（[IPython](http://ipython.org/) でも使用されている）を組み合わせたものです。この組み合わせにより、Jupyter/IPython の強力な [グラフィカルノートブック](http://ipython.org/notebook.html) を使用して、Julia 言語と対話することができます。これは、コード、フォーマットされたテキスト、数学、マルチメディアを単一のドキュメントに統合しています。

`IJulia` モジュールは、3つの方法で使用されます。

  * `using IJulia; notebook()` と入力すると、ウェブブラウザで Jupyter ノートブックインターフェースが起動します。これは、オペレーティングシステムのコマンドラインから直接 `jupyter notebook` を起動する代替手段です。
  * 実行中のノートブックでは、`IJulia` モジュールがロードされ、`IJulia.somefunctions` を使用して実行中の IJulia カーネルと対話できます：

      * `IJulia.load(filename)` と `IJulia.load_string(s)` は、それぞれファイルまたは文字列の内容をノートブックセルにロードします。
      * `IJulia.clear_output()` はノートブックセルの出力をクリアします。これは、シンプルなアニメーションに便利です。
      * `IJulia.clear_history()` は、履歴変数 `In` と `Out` をクリアします。
      * `push_X_hook(f)` と `pop_X_hook(f)`、ここで `X` は `preexecute`、`postexecute`、または `posterror` のいずれかです。これにより、ノートブックセルが評価されるときに実行される関数のリストに「フック」関数を挿入できます。
      * `IJulia.set_verbose()` は、IJulia が内部で何をしているかについての詳細な出力を有効にします。これは主にデバッグに使用されます。
  * Jupyter サーバーと通信する際に、IJulia カーネルによって内部的に使用されます。
