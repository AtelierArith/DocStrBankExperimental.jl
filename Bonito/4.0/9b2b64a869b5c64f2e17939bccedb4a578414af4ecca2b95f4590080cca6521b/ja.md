```
Page(;
    offline=false, exportable=true,
    connection::Union{Nothing, FrontendConnection}=nothing,
    server_config...
)
```

Pageは、Pluto/IJulia/Documenterのようなマルチページ表示出力でBonitoの状態をリセットするために使用できます。Documenterの場合、ページは`exportable=true, offline=true`に設定する必要がありますが、Pageは既知のパッケージの最も一般的なパラメータにデフォルト設定されるため、設定する必要はありません。Exportableは、すべてのデータとjs依存関係をインライン化する効果があり、すべてを単一のHTMLオブジェクトで読み込むことができます。`offline=true`は、Pageが実行中のJuliaプロセスに接続しようとさえしないようにし、Documenterで行う静的エクスポートの種類に対して理にかなっています。便利のために、追加のサーバー設定を渡すこともでき、これらは直接`configure_server!(;server_config...)`に配置されます。パラメータを確認するには、`configure_server!`のドキュメントを参照してください。
