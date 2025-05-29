```julia
publish(
;
    prerender,
    minify,
    nopass,
    prepath,
    message,
    cleanup,
    final,
    do_push
)

```

これは、あまり派手ではない git commit と git push を行うシンプルなラッパーです。現在のディレクトリが git フォルダーであることを前提としています。また、`prepath`（または `config.md` に設定されている場合）を指定すると、すべてのリンクが修正されます。

**キーワード引数**

  * `prerender=true`: プッシュ前に JavaScript をプリレンダリングします。詳細は [`optimize`](@ref) を参照してください。
  * `minify=true`: プッシュ前に出力をミニファイします。詳細は [`optimize`](@ref) を参照してください。
  * `nopass=false`: すでに手動で `optimize` を実行している場合は、これを true に設定します。
  * `prepath=""`: プロジェクトページの場合は "project-name" のようなものに設定します。
  * `message="franklin-update"`: コミットメッセージを追加します。
  * `cleanup=true`: 環境辞書をクリーンアップするかどうか（true のままにするべきです）。
  * `final=nothing`: git push の前に最後に実行する関数 `()->nothing`。Lunr インデックスを更新したり、Literate でノートブックファイルを生成したりするために使用できます。Franklin によってエクスポートされる `fdf_*` 関数を組み合わせることを検討するか、それらを模倣することができます。GLOBAL_VARS にアクセスできます。
