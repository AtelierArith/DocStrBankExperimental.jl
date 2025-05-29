```julia
serve(
;
    clear,
    verb,
    port,
    single,
    prerender,
    nomess,
    isoptim,
    no_fail_prerender,
    eval_all,
    silent,
    cleanup
)

```

現在のディレクトリでJuDocを実行します。

キーワード引数:

  * `clear=false`:     既存の出力ディレクトリを削除するかどうか
  * `verb=false`:      メッセージを表示するかどうか
  * `port=8000`:       ローカルサーバーに使用するポート（8000から9000の間の番号を選択する必要があります）
  * `single=false`:    単一のパスを実行するか、継続的に実行するか
  * `prerender=false`: JavaScript（KaTeXおよびhighlight.js）を事前レンダリングするかどうか
  * `nomess=false`:    すべてのメッセージを抑制します（内部使用）。
  * `isoptim=false`:   最適化フェーズにいるかどうか（そうであれば、プロジェクトウェブサイトの場合にリンクが固定されます、[`write_page`](@ref)を参照）。
  * `no_fail_prerender=true`: 事前レンダリングフェーズでエラーを無視し、出力を生成しようとするかどうか
  * `eval_all=false`:  すべてのコードブロックの再評価を強制するかどうか
  * `silent=false`:    すべての出力（評価ステートメントを含む）を抑制するためにこれをオンにします。
  * `cleanup=true`:    環境辞書をクリアするかどうか、[`cleanup`](@ref)を参照。
