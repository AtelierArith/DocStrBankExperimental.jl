GMTは、地理データセットとデカルトデータセット（フィルタリング、トレンドフィッティング、グリッド化、投影などを含む）を操作し、高品質のイラストを生成します。

GMT.jlのドキュメントは https://www.generic-mapping-tools.org/GMTjl_doc にあります。

---

GMT.jlのデフォルトはGMT_jllアーティファクトを使用することです。ただし、これをシステム全体のGMTインストールを使用するように変更できます。すべての情報は、`deps/build.jl`からコンパイルによって作成される`deps/deps.jl`ファイルに保存されます。システム全体のGMTインストールに切り替えるには、REPLで次のようにします：

  * ENV["SYSTEMWIDE_GMT"] = 1;
  * import Pkg; Pkg.build("GMT")
  * Juliaを再起動

上記は、他の理由でJuliaの再コンパイルがトリガーされるまで機能します。その場合、JLLアーティファクトが再び使用されます。ENV["SYSTEMWIDE*GMT"] = 1の解決策を永続的にするには、.bashrc（またはその他のファイル）に「SYSTEMWIDE*GMT」環境変数を永続的に宣言してください。
