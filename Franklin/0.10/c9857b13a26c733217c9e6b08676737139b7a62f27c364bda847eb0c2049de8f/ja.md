```julia
serve(
;
    clear,
    verb,
    port,
    single,
    prerender,
    nomess,
    is_final_pass,
    no_fail_prerender,
    eval_all,
    silent,
    cleanup,
    on_write,
    log,
    host,
    show_warnings,
    fail_on_warning,
    launch,
    no_set_paths,
    join_to_prepath
)

```

現在のディレクトリでFranklinを実行します。

キーワード引数:

  * `clear=false`:            既存の出力ディレクトリを削除するかどうか
  * `verb=false`:             メッセージを表示するかどうか
  * `port=8000`:              ローカルサーバーに使用するポート（8000から9000の間の番号を選択する必要があります）
  * `single=false`:           単一パスで実行するか、継続的に実行するか
  * `nomess=false`:           すべてのメッセージを抑制します（内部使用）。
  * `is_final_pass=false`:    "最終パス"にいるかどうか（そうであれば、プロジェクトウェブサイトの場合にリンクが修正されます、[`convert_and_write`](@ref)を参照）。
  * `prerender=false`:        javascript（KaTeXおよびhighlight.js）を事前レンダリングするかどうか
  * `no_fail_prerender=true`: 事前レンダリングフェーズでエラーを無視し、出力を生成しようとするかどうか
  * `eval_all=false`:         すべてのコードブロックの再評価を強制するかどうか
  * `silent=false`:           すべての出力（評価文を含む）を抑制するためにこれをオンにします。
  * `cleanup=true`:           環境辞書をクリアするかどうか、[`cleanup`](@ref)を参照。
  * `on_write(pg, fd_vars)`:  ページがレンダリングされた後のコールバック関数で、レンダリングされたページとページ変数を引数として渡します
  * `host="127.0.0.1"`:       ローカルサーバーに使用するホスト
  * `show_warnings=true`:     franklinの警告を表示するかどうか
  * `launch=!single`:         サービング時にブラウザを起動するかどうか
