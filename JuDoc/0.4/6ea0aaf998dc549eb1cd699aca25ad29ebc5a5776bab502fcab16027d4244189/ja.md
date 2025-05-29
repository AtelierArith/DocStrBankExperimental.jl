```julia
publish(
;
    prerender,
    minify,
    nopass,
    prepath,
    message,
    cleanup,
    final
)

```

これは、あまり手の込んだことなく git commit と git push を行うシンプルなラッパーです。現在のディレクトリが git フォルダーであることを前提としています。また、`prepath`（または `config.md` に設定されている場合）を指定すると、すべてのリンクを修正します。

**キーワード引数**

  * `prerender=true`:      プッシュ前に JavaScript をプリレンダリングします。詳細は [`optimize`](@ref) を参照してください。
  * `minify=true`:         プッシュ前に出力をミニファイします。詳細は [`optimize`](@ref) を参照してください。
  * `nopass=false`:        すでに手動で `optimize` を実行した場合は、これを true に設定します。
  * `prepath=""`:          プロジェクトページの場合は "project-name" のようなものに設定します。
  * `message="jd-update"`: コミットメッセージを追加します。
  * `cleanup=true`:        環境辞書をクリーンアップするかどうか（true のままにするべきです）。
  * `final=nothing`:       git push の前に最後に実行する関数 `()->nothing`。Lunr インデックスを更新したり、Literate でノートブックファイルを生成したりするのに使用できます。`jdf_*` 関数を作成することを検討するか、JuDoc によってエクスポートされた関数を模倣することができます。GLOBAL*PAGE*VARS にアクセスできます。
